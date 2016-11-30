---
layout: post
title: "Learning Python 018 Python2 和 Python3 中 range()函数的使用"
date: 2016-11-30 13:37:04 +0800
comments: true
sharing: true
categories: [python]
tags: [Python, Python3, range(), list, 生成器]
---



---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 2.7.10 和 python 3.5.0

---

## `range()` 函数

* Python2中：用来创建一个列表（list）。
* Python3中：用来创建一个可以生成list或者tuple的生成器。

## Python2 `range()`函数 知识点

Python2 中的`range()` 函数可以生成一个list。（分配内存空间）

```python
a = range(10)
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
b = range(4,10)
# [4, 5, 6, 7, 8, 9]
```



----------

Python2 中的`xrange()`函数不是生成一个list，而是生成一个生成器，不分配内存。

```python
a = xrange(10)
# xrange(10)
b = list(xrange(10))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
c = tuple(xrange(10))
# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```


----------


## Python3 `range()`函数 知识点


----------

```python
a = range(10)
# range(0, 10)
```

输出：（打印出来的不是一个列表，而是一个生成器）。

Python3 选择这样做的原因：可以节约内存空间，详情请参考这篇博客：[Python2和Python3的内存释放](http://www.aobosir.com/blog/2016/11/30/python2-python3-Memory-release-gc/)。

Python3中的`range()`函数的功能和Python2中的`xrange()`函数一样，所以在Python3中没有`xrange()`函数。

----------

要想生成**list**或者**tuple**，这样做：
```python
a = list(range(10))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
b = list(range(4,10))
# [4, 5, 6, 7, 8, 9]

a = tuple(range(10))
# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
b = tuple(range(4,10))
# (4, 5, 6, 7, 8, 9)
```



----------

## `range()`函数的使用

下面这段代码在Python2 和 Python3中得到的运行结果都是一样的。

```python
for i in range(10):
    print(i)
```

输出：

```
0
1
2
3
4
5
6
7
8
9
```

运行结果是一样的，但是运行的原理不同：

* Python2：在第一次执行 `range(10)`，就生成了一个`[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`列表。
* Python3：在每次执行`range(10)`时，生成一个元素`i`。