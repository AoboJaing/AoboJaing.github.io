---
layout: post
title: "Learning Python 022 调用DOS命令 --- 实例：调用Windows里面的copy命令"
date: 2016-12-1 05:47:12 +0800
comments: true
sharing: true
categories: [python]
tags: [Python, DOS, Windows, os, copy]
---

---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 2.7.10 和 python 3.5.0

---

> 本篇博客对 Python2 和 Python3 都适用。


----------


## 实例：调用Windows里面的`copy`命令

比如现在，我想把这个路径`F:\原文件夹`里面的所有文件复制到这个路径`F:\目标文件夹`里面。可以在**DOS**命令行窗口里面执行：

```
copy "F:\原文件夹\*" "F:\目标文件夹\"
```

所以，我们要使用Python调用DOS命令行工具的步骤就两步：

1. 构造命令字符串。
2. 使用`os.system()`函数执行命令字符串。


----------


我们使用python调用Windows系统DOS命令行里面的**copy**工具来进行文件的复制。代码如下：

适合在Python3中执行的代码：

```python
# -*- coding: utf-8 -*-

import os

org_folder = r'F:\原文件夹'
res_folder = r'F:\目标文件夹'

# 构造命令字符串
copy_command = 'copy "' + org_folder + r'\*" "' + res_folder + r'\"'
# copy_command = copy_command.decode('utf-8').encode('GB18030')
print(copy_command) # 如果你使用的是Python2，需要将这一行的注释去掉。
# print(copy_command)
# 使用os.system()函数执行命令字符串
os.system(copy_command)
```


上面的代码如果在python2中执行，不将第10行的注释去掉的话，会因为字符串编码和解码的不正确问题，导致系统找不到指定的路径。：

```
copy "F:\鍘熸枃浠跺す\*" "F:\鐩爣鏂囦欢澶筡"
系统找不到指定的路径。
```



---



## 经验：我发现了两件事：

**第一件事 .** 在**DOS** 里面，执行下面的命令，有的是对的，有的是错的：

```
# Succesfull
copy "F:\原文件夹\*" "F:\目标文件夹\"
# Succesfull
copy "F:\原文件夹\\*" "F:\目标文件夹\\"

# error
copy "F:/原文件夹/*" "F:/目标文件夹/"
# error
copy "F://原文件夹//*" "F://目标文件夹//"
```

总结：

1. `\`是一个特殊字符，它不能再字符串中正常的显示，如果必须显示，就这样写：`\\`
2. **DOS** 命令里面指定文件路径时，只能使用`\`，不能使用`/` 和 `//` ，使用这两个都是错的，都会导致 **DOS**找不到指定的文件路径
3. 在**DOS** 命令里面，指定文件路径的 `\` ，你写成 `\\` 或者 `\\\` 或者 `\\\\\\` ... 对是可以正常执行的，不会出现错误。

---

**第二件事 .** 同时，我发现：

python 的字符串前面加上`r`，说明这个字符串是`raw string`，即无需转义的字符串，意思就是这个字符串里面有什么就是什么。

但是我发现了python的一个bug：

```python
# error
str = r'D:\WorkSpace\test_ws\'
# 经验：就算是在字符串前面加上了 r ，字符串最后一个字符也不能是 /
```


```python
# succes
str = r'D:\WorkSpace\test_ws\\'
print(str)
# 输出：D:\WorkSpace\test_ws\\
```

```python
# succes,但是不是我们要的结果
str = 'D:\WorkSpace\test_ws\\'
print(str)
# 输出：D:\WorkSpace	est_ws\
```


----------



