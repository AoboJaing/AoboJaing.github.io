---
layout: post
title: "Learning Python 019 生成器（Generators）和 yield"
date: 2016-11-30 23:17:17 +0800
comments: true
sharing: true
categories: [python]
tags: [Python, Python3, 生成器, Generators, yield]
---


---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 2.7.10 和 python 3.5.0

---

## 知识点：生成器

[生成器只能用于迭代操作。](http://python3-cookbook.readthedocs.io/zh_CN/latest/c04/p03_create_new_iteration_with_generators.html) 

一个函数，其中带 `yield` 	关键字的代码，它不会执行，只是记下有这个操作；其他代码正常的执行。而被记下的这些操作会像队列一样存起来，这个“队列”就是 **生成器**，并且会类似于`return`一样返回。

一个函数的代码里面有 `yield` 关键字，那么这个函数就是一个**制造生成器的函数**。

> 生成器是Python中的高级特性。我之前学习过，还写了一个博客：[Learning Python 011 高级特性 2](http://blog.csdn.net/github_35160620/article/details/51985596?locationNum=1&fps=1)

----------

## Python3 例子

```python
>>> def f():
...     yield 1
...     yield 2
...     yield 3
...
```

```python
>>> g = f()
>>> g
<generator object f at 0x0000023B63151258>
>>> type(g)
<class 'generator'>
>>> next(g)
1
>>> next(g)
2
>>> next(g)
3
>>> next(g)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
>>> list(g)
[]
>>> g = f()
>>> list(g)
[1, 2, 3]
>>> list(g)
[]
>>>
```


----------

```python
>>> def counter(num):
...     print('Run to the ' + str(num) + ' yield')
...
>>> def f():
...     print('start!')
...     yield counter(1)
...     yield counter(2)
...     yield counter(3)
...     print('Done!')
...
```

```python
>>> g = f()
>>> g
<generator object f at 0x000001D4843E1258>
>>> next(g)
start!
Run to the 1 yield
>>> next(g)
Run to the 2 yield
>>> next(g)
Run to the 3 yield
>>> next(g)
Done!
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
>>> list(g)
[]
>>> g = f()
>>> list(g)
start!
Run to the 1 yield
Run to the 2 yield
Run to the 3 yield
Done!
[None, None, None]
>>>
```


----------

## Python2 实例

生成器在 python2 的用法和在python3中的用法一样，唯一的区别是：

* python2 中 可以使用`next(g)` 或者 `g.next()`。 这样两个等价
* python3 中 只有`next(g)`，没有`g.next()`。


----------

参考网站：[生成器](http://wiki.jikexueyuan.com/project/start-learning-python/215.html)