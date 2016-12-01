---
layout: post
title: "Learning Python 025 字符串分割"
date: 2016-12-1 17:06:32 +0800
comments: true
sharing: true
categories: [python]
tags: [字符串, python3, 分割, split, python]
---


---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python2.7.10 或者 python 3.5.0

---

> 本博文对Python2和Python3都适用。
 
----------


参考网站：[Python split()方法](http://www.runoob.com/python/att-string-split.html)


Python split()通过指定分隔符对字符串进行切片，返回一个列表。


## 语法：

```python
zifuchuang.split(str, num)
```

* str 分隔符
* num 分割次数

## 实例：

```python
str = r'D:\WorkSpace\test_ws\Git(GitHub)'
l = str.split('\\')
print(l)
print(str.split('\\', 1))
```

输出：

```
['D:', 'WorkSpace', 'test_ws', 'Git(GitHub)']
['D:', 'WorkSpace\\test_ws\\Git(GitHub)']
```