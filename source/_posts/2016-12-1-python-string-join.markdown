---
layout: post
title: "Learning Python 026 字符串连接"
date: 2016-12-01 19:03:50 +0800
comments: true
sharing: true
categories: [python]
tags: [python3, python2, str, 字符串, 连接, join]
---

---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python2.7.10 或者 python 3.5.0

---

> 本博文对Python2和Python3都适用。

----------

参考网站：[Python 字符串操作（string替换、删除、截取、复制、连接、比较、查找、包含、大小写转换、分割等）](http://www.cnblogs.com/huangcong/archive/2011/08/29/2158268.html)

```python
# -!- coding: utf-8 -!-

path = r'D:\WorkSpace\test_ws\笔记\text.md'
delimiter = '\\'

mylist = path.split(delimiter)
res_path = delimiter.join(mylist[:-1])
# res_path = res_path.decode('utf-8').encode('GB18030') # 如果是适用python2在windows系统上运行，需要将这样注释去掉，否则你会得到中文乱码
print(res_path)
```

运行输出：

```
D:\WorkSpace\test_ws\笔记
```
