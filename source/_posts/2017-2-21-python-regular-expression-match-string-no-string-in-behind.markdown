---
layout: post
title: "Learning Python 008 正则表达式-007 匹配的字符串模板中如果只有前面有字符串，而后面没有字符串时，这个匹配模板要怎么写"
date: 2017-02-21 01:19:10 +0800
comments: true
sharing: true
categories: [Python, 正则表达式]
tags: [Python, 正则表达式, re]
---

---

## 开发环境

* Python第三方库：lxml、Twisted、pywin32、scrapy
* Python 版本：python-3.5.0-amd64
* PyCharm软件版本：pycharm-professional-2016.1.4
* 电脑系统：Windows 10 64位

如果你还没有搭建好开发环境，请到[这篇博客](http://www.aobosir.com/blog/2016/11/26/python3-large-web-crawler-001-Build-development-environment/)。

---


## 

例子程序在这里：[learning_python_08_06.py](https://github.com/AoboJaing/learning_python/blob/master/learning_python08_06.py)

参考网站：[python正则表达式详解](http://www.cnblogs.com/dyfblog/p/5880728.html)

![Alt text](/images/2017-2-21-python-regular-expression-match-string-no-string-in-behind/1487610263474.png)

当我们的匹配字符串的末尾处没有字符串的时候，我们使用`\Z`来表示结束处。

> 同样的道理：当我们的匹配字符串的开头处没有字符串的时候，我们使用`\A`来表示开头处。


```python
# -!- coding:utf-8 -!-

import re

# Learning Python 008 正则表达式-007 匹配的字符串模板中如果只有前面有字符串，而后面没有字符串时，这个匹配模板要怎么写 --- 2017年2月20日 星期一
# 博文的链接地址：http://www.aobosir.com/blog/2017/02/21/python-regular-expression-match-string-no-string-in-behind/

# 这个程序的功能：获取'.\data\2017-2-19-3D-printer-hot-bed.markdown'文件里面所有的图片链接的地址。

# 这个demo 程序使用了两次正则表达式的方式，成功的将所有的图片链接地址都获取了出来。（其中有："![Alt text](/images/2017-2-21-python-regular-expression-match-string-no-string-in-behind/1485166773479.png)"这种形式的，还是"![Alt text | 240x0](./1485166756931.png)"这种形式的。）

file = open(r'.\data\2017-2-19-3D-printer-hot-bed.markdown', 'rt', encoding='utf-8')
data = file.read()
print(data)

image_local_path_step1 = re.findall('!\[Alt text(.*?)\)', data, re.S)
for i in range(len(image_local_path_step1)):
    print(image_local_path_step1[i])
    pass

for i in range(len(image_local_path_step1)):
    image_local_path_step1_this = image_local_path_step1[i]
    image_local_path_step2 = re.findall(']\((.*?)\Z', image_local_path_step1_this, re.S)
    print(image_local_path_step2[0])
    pass


file.close()
```

这个demo程序中，使用了两层正则表达式。

第一层的匹配字符串是：`!\[Alt text(.*?)\)`。它可以得到`](./1485164492501.png`这样或者` | 240x0](./1485166756931.png`这样的结果。

解决我们将得到的结果再进行一次正则表示匹配。这次使用的匹配字符串是：`]\((.*?)\Z`。通过这次匹配，得到的结果就都是图片的地址了。（想这样：`./1485181859693.png`）

> 注意：在匹配字符串中的`(`和`)`需要使用转义字符`\`修饰。
