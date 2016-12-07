---
layout: post
title: "Learning Python 008 正则表达式-005 compile模板的使用"
date: 2016-12-08 07:05:09 +0800
comments: true
sharing: true
categories: [python, 正则表达式]
tags: [python, compile, 模式匹配, 正则表达式]
---

---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 2.7.10 和 python 3.5.0

---

## compile()函数的用法

```python
import re
str = 'fdfgdrthxxi--gdfgexxlove--dsdfwesdxxyou--dfgdf'
pattam_str = 'xx(.*?)--'
result = re.compile(pattam_str).findall(str)
print(result)
```

运行：

```
>python learningpython29.py
['i', 'love', 'you']
```

解释：

* 其中`pattam_str` 就是**正则表达式**字符串。
* `str` 就是目标字符串
* `result` 就是得到的结果

代码中的

```python
result = re.compile(pattam_str).findall(str)
print(result)
```

等价于：

```python
result = re.findall(pattam_str, str)
```

运行输出的结果是一样的。


----------
