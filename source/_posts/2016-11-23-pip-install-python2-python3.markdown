---
layout: post
title: "Learning Python 014 使用 pip 工具的注意事项 --- 混淆的python2 和 python3"
date: 2016-11-23 00:24:01 +0800
comments: true
sharing: true
categories: [python]
tags: [Python2, pip, Python3]
---


---

**Q : ** 如果你的电脑之前安装了Python2，那么Python2 有自己的pip工具，Python3 也是有自己的pip工具，所以，如果你在DOS命令行上执行`pip install some-package-name`命令的时候，系统会使用哪个pip工具呢？是python2的pip，还是python3的pip？
 
**A : ** 如果你先安装的是python2，后安装的python3，那么系统默认使用python2的pip；反之，如果你先安装的是python3，后安装的python2，那么系统默认安装的是python3的pip。

**解决方法 ： ** 为了避开这个问题，我们在使用 pip 工具时，使用绝对路径：

**使用 python2 的 pip**

```
cd C:\Python27\Scripts
pip.exe install some-package-name
```

**使用 python3 的 pip**

```
cd C:\Users\AOBO\AppData\Local\Programs\Python\Python35\Scripts
pip.exe install some-package-name
```

