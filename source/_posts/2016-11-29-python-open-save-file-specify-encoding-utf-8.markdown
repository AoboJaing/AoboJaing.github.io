---
layout: post
title: "Learning Python 016 写文件时，将其用指定的编码方式保存（比如：UTF-8无BOM编码方式）"
date: 2016-11-29 20:13:51 +0800
comments: true
sharing: true
categories: [python]
tags: [Python, open, 编码方式, 写文件]
---

---

* 使用的电脑系统：Windows 10 64位
* 使用的开发集成环境：PyCharm 2016.1.4
* 使用的Python的版本：python 3.5.0

---

## 学习这个知识点的原因

举一个实例：

**Octopress**站点路径里面博文文件（`.markdown`后缀文件）必须要是以UTF-8无BOM编码方式编码的文件，否则执行`rake generate`命令会出现下面这个错误：

![Alt text](/images/2016-11-29-python-open-save-file-specify-encoding-utf-8/1480419391696.png)

```
Error reading file F:/octopress/source/_posts/xxxx.markdown: invalid byte sequence in UTF-8
  Liquid Exception: invalid byte sequence in UTF-8 in _posts/xxxx.markdown/#excerpt
```

所以，为了解决不要出现这个问题，我们需要将文件指定你希望的编码方式保存。

## 将其用指定的编码方式保存（比如：UTF-8无BOM编码方式）

其实很简单，我们只需要这样做：

```python
file = open(file_path, 'w', encoding='utf-8')
```

这样`file`文件就是以**Utf-8无BOM编码方式**编码的文件。

> 我们也看到了，其实不是将`file`保存为以**Utf-8无BOM编码方式**编码的文件，而是创建这个一个以**Utf-8无BOM编码方式**编码的文件 `file`。





