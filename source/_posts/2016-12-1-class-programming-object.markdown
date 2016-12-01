---
layout: post
title: "Learning Python 023 类编程"
date: 2016-12-1 07:03:26 +0800
comments: true
sharing: true
categories: [python]
tags: [Python, python3, 类编程, 对象]
---


---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 3.5.0

---


# 怎么使用python编写一个 **类**

参考网站：[Python3-cookbook 类与对象](http://python3-cookbook.readthedocs.io/zh_CN/latest/c08/p01_change_string_representation_of_instances.html)

随便编写一个Python类，类里面至少有下面三个函数：

```python
class Pair:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        return 'Pair({0.x!r}, {0.y!r})'.format(self)

    def __str__(self):
        return '({0.x!s}, {0.y!s})'.format(self)
```

* `__init__()` 函数就是类的构造函数。
* `__repr__()`  和 `__str__()` 函数 都是用来输出字符串用的。

```python
>>> p = Pair(3, 4)
>>> p
Pair(3, 4) # __repr__() output
>>> print(p)
(3, 4) # __str__() output
>>>
```


----------


