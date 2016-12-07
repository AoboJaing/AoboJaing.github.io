---
layout: post
title: "Python3 解决编码问题：  UnicodeEncodeError: 'gbk' codec can't encode character '\\xa9' in position xxx: illegal multibyte sequence --- 当执行爬虫将爬取信息打印到终端时出现的编码错误"
date: 2016-12-08 06:38:45 +0800
comments: true
sharing: true
categories: [Python3 大型网络爬虫实战]
tags: [python3 ,UnicodeEncodeError, \xa9, gbk, 编码问题, Unicode]
---


---

## 开发环境

* Python第三方库：lxml、Twisted、pywin32、scrapy
* Python 版本：python-3.5.0-amd64
* PyCharm软件版本：pycharm-professional-2016.1.4
* 电脑系统：Windows 10 64位

如果你还没有搭建好开发环境，请到[这篇博客](http://www.aobosir.com/blog/2016/11/26/python3-large-web-crawler-001-Build-development-environment/)。

---

当使用Scrapy写爬虫项目的时候，当我们爬取某些中文网站，然后在DOS终端中打印爬取的网页源代码的时候，会出现各式各样的编码错误，今天，我又遇到一种编码错误，下面我将这个错误和对应的解决办法记录下来。

爬取的目标网址：http://blog.csdn.net/github_35160620/article/details/53353672

出现错误的代码：

```python
    def next(self, response):
        body_data = response.body.decode('utf-8', 'ignore')
        print(body_data)
        pass
```

执行：来到对应的爬虫项目路径下，执行：

```
scrapy crawl 爬虫名字
```

在出现的调试信息中你可以看到一个编码错误：

```
    print(body_data)
UnicodeEncodeError: 'gbk' codec can't encode character '\xa9' in position 6732: illegal multibyte sequence
```

通过查看，这个[`u'xa9'` Unicode编码所表示的字符是：`©`](http://www.codetable.net/hex/a9)。

![Alt text](/images/2016-12-8-python3-UnicodeEncodeError-gbk-codec-can't-encode-character-xa9/1481149755580.png)


可以解决这个错误的方法：

将上面的代码修改为：

```python
    def next(self, response):
        body_data = response.body.decode('utf-8', 'ignore').replace(u'\xa9', u'')
        print(body_data)
        pass
```

现在运行这个程序`scrapy crawl 爬虫名字 --nolog`，上面的编码错误就没有。成功的输出了爬取的网页的源代码。

