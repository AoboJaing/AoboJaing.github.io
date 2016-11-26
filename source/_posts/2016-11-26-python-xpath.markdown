---
layout: post
title: "Python --- xpath 表达式 --- Ongoing"
date: 2016-11-26 18:00:15 +0800
comments: true
sharing: true
categories: [Python3 大型网络爬虫实战]
tags: [xpath ,爬虫, python]
---


---


## 什么是 **XPath**？

参考网站：http://www.w3school.com.cn/xpath/xpath_intro.asp

XPath 是一门在 XML 文档中查找信息的语言。XPath 用于在 XML 文档中通过元素和属性进行导航。

## xpath 表达式 语法讲解

参考网站：http://www.w3school.com.cn/xpath/xpath_syntax.asp


例如，现在有这些信息：

```
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>CSDN.NET - 全球最大中文IT社区，为IT专业技术人员提供最全面的信息传播和服务平台</title>
<link href="http://c.csdnimg.cn/www/css/csdn_common.css" rel="stylesheet" type="text/css">
<link href="css/content.css" rel="stylesheet" type="text/css">
<link href="http://c.csdnimg.cn/public/favicon.ico" rel="SHORTCUT ICON">
</head>
```

| 表达式|     意思|
| :-------- | --------:|
|/ |寻找指定标签|
|//| 寻找所有标签|
|@| 提取某个标签的属性的内容 |


---

**例子：**

不管怎么样，记住一点：**只有唯一的东西才能定位**。

```python
/title.text()
```

表示：

```
CSDN.NET - 全球最大中文IT社区，为IT专业技术人员提供最全面的信息传播和服务平台
```


----------


参考网站：http://scrapy-chs.readthedocs.io/zh_CN/0.24/topics/selectors.html

---

