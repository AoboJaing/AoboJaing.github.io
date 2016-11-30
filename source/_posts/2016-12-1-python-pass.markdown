---
layout: post
title: "Learning Python 020 pass 的用法"
date: 2016-12-1 04:12:13 +0800
comments: true
sharing: true
categories: [python]
tags: [Python, pass]
---


---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 2.7.10 和 python 3.5.0

---

## pass 的用法

参考网站：[Python pass 语句](http://www.runoob.com/python/python-pass-statement.html)

> Python2 和 Python3 中 pass 的用法都是一样的。

`pass` 就是一个空语句，没有任何实际意义，作用是保存程序结构的完整性。

因为Python不像C/C++语言那样，定义一个代码块使用 `{}`。Python是使用**缩进**的形式来表述一个代码块的。

比如说想C语言里面的下面这段代码，如果换成Python，怎么写呢？

```cpp
while(1){
}
```

换成Python，这样写：

```python
while True:
	pass
```


----------
