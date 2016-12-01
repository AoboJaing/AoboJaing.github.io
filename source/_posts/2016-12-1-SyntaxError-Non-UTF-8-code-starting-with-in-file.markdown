---
layout: post
title: "Learning Python 027 解决错误：SyntaxError: Non-UTF-8 code starting with \'\\xc8\' in file xxxx.py"
date: 2016-12-1 17:37:34 +0800
comments: true
sharing: true
categories: [python]
tags: [python, SyntaxError, Non-UTF-8, 解决错误]
---



---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python2.7.10 或者 python 3.5.0

---

> 本博文对Python2和Python3都适用。


----------

出现这个错误，是因为`xxxx.py` 文件里面有中文字符。

解决办法：在文件第一行，加上下面的代码：

```python
# -!- coding: utf-8 -!-
```

