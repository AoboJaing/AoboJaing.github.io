---
layout: post
title: "Learning Python 017 — Python2 和 Python3 的内存释放"
date: 2016-11-30 13:34:56 +0800
comments: true
sharing: true
categories: [python]
tags: [Python, Python3, 内存释放, gc, 优化内存空间]
---

---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 2.7.10 和 python 3.5.0

---

## 学习Python的内存释放知识点的动机

之前我学过很多Python的程序，偶然的一次，我打开任务管理器，看到我写的程序，运行时占用了大量的内存，所以，我希望学会如何释放内存，来优化我的程序，也不给电脑照成太大的负担，所以，我想学会：Python的内存释放这个知识点。


----------

参考网站： [gc模块–Python内存释放](http://qinqianshan.com/python-memory-the-gc-module-released/)

下面写几个实验程序，里面都是使用`range()` 函数来分配内存空间的。`range()`函数的详细介绍，请见这篇博客：[range()函数在python2 和 python3中的使用介绍](http://www.aobosir.com/blog/2016/11/30/python2-python3-range-function/)。


## Python2 内存释放

未优化前的代码：

```python
a = range(1000*10000)
while True:
	pass
```

![Alt text](/images/2016-11-30-python2-python3-Memory-release-gc/1480424648330.png)


----------

优化内存的代码：

使用手动释放内存的方法来优化内存。

```python
import gc
a = range(1000*10000)
del a
gc.collect()
while True:
	pass
```

可以看出，占用的内存空间明显减小了。

![Alt text](/images/2016-11-30-python2-python3-Memory-release-gc/1480424705571.png)


----------

既优化了内存，也优化了CPU 的代码

使用睡眠来优化CPU运行。

```python
import gc
import time

a = range(1000*10000)
del a
gc.collect()
while True:
	time.sleep(1.0)
	pass
```

![Alt text](/images/2016-11-30-python2-python3-Memory-release-gc/1480424877933.png)


----------

## Python3 内存释放

未优化前的代码：


```python
a = range(1000*10000)
while True:
	pass
```

使用Python3库运行未优化的代码，所需要的消耗的内存空间和使用Python2运行优化内存的代码消耗的内存空间 差不多。

![Alt text](/images/2016-11-30-python2-python3-Memory-release-gc/1480433041923.png)


----------

优化内存的代码：


```python
import gc
a = range(1000*10000)
del a
gc.collect()
while True:
	pass
```

可以看出，所暂用的内存空间没有任何增减。

![Alt text](/images/2016-11-30-python2-python3-Memory-release-gc/1480432975323.png)


----------

既优化了内存，也优化了CPU 的代码：



```python
import gc
import time

a = range(1000*10000)
del a
gc.collect()
while True:
	time.sleep(1.0)
	pass
```

![Alt text](/images/2016-11-30-python2-python3-Memory-release-gc/1480432888777.png)


----------

## 总结

Python3 真的是比 Python2 更加的完善了，从这一点上也可以看出来，Python语言是第4代语言里面非常杰出的语言。随着它的不断发展，它会运行速度慢和内存消耗大的缺点会慢慢的消失（因为：[许多Python内置库是用C语言写的](http://python3-cookbook.readthedocs.io/zh_CN/latest/chapters/p15_c_extensions.html)）。我看好Python。
