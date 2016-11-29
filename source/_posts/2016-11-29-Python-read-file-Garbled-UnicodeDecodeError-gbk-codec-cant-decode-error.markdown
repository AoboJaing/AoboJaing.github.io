---
layout: post
title: "Learning Python 015 解决问题：读取文件时，出现乱码或者“UnicodeDecodeError  \'gbk\' codec can\'t decode byte 0xXX in position XX: incomplete multibyte sequence” 错误"
date: 2016-11-29 19:18:27 +0800
comments: true
sharing: true
categories: [Python]
tags: [python, 乱码, UnicodeDecodeError, gbk, 读取文件, 编码]
---


---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 3.5.0

---

## 出现的错误

读取文件时，出现**乱码**或者`UnicodeDecodeError: 'gbk' codec can't decode byte 0xXX in position XX: incomplete multibyte sequence` 错误

----------


## 出现错误的原因

这两个错误可能会出现一个，两个错误的出现的原因是一样的：当我们使用了一个不正确的编码方式去读取一个不是用这个编码方式编码的文件时，轻者出现乱码，重者出现`UnicodeDecodeError`错误。

----------


## 模拟错误发生现场

```python
file = open('newfile.txt', 'w', encoding='utf-8')
file.write('你好，AoboSir.')
file.close()
file = open('newfile.txt', 'r')
print(file.read())
file.close()
```

运行输出：

```
浣犲ソ锛孉oboSir.
```

----------


```python
file = open('newfile.txt', 'w', encoding='utf-8')
file.write('你好，AoboSir。')
file.close()
file = open('newfile.txt', 'r')
print(file.read())
file.close()
```

运行输出：

```
Traceback (most recent call last):
  File "D:/WorkSpace/test_ws/demo/learning_python_15.py", line 6, in <module>
    print(file.read())
UnicodeDecodeError: 'gbk' codec can't decode byte 0x82 in position 35: incomplete multibyte sequence
```

----------


## 解决办法

读取文件时，指定正确的编码方式：

```python
file = open('newfile.txt', 'r', encoding='utf-8')
```

现在再运行，就正常了：

```
你好，AoboSir。
```


----------


## 搞定

