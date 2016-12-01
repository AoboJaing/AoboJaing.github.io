---
layout: post
title: "Learning Python 024 判断文件和文件夹是否存在"
date: 2016-12-1 08:46:09 +0800
comments: true
sharing: true
categories: [python]
tags: [文件, 文件夹, 判断, exists]
---


---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python2.7.10 或者 python 3.5.0

---

## 判断文件

```python
import os
a = os.path.isfile(r'D:\WorkSpace\test_ws\ao.txt')
print(a)
```

或者下面的代码。（这两种方式是对于判断一个文件是否存在是等价的。）

```python
import os
a = os.path.exists(r'D:\WorkSpace\test_ws\ao.txt')
print(a)
```

----------


## 判断文件夹

```python
import os
a = os.path.exists(r'D:\WorkSpace\test_ws')
print(a)
```