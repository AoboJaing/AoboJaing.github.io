---
layout: post
title: "Python3 大型网络爬虫实战 — 给 scrapy 爬虫项目设置为防反爬"
date: 2016-12-06 00:04:35 +0800
comments: true
sharing: true
categories: [Python3 大型网络爬虫实战]
tags: [Python3, Scrapy, 爬虫, 防反爬, settings]
---

---

## 开发环境

* Python第三方库：lxml、Twisted、pywin32、scrapy
* Python 版本：python-3.5.0-amd64
* PyCharm软件版本：pycharm-professional-2016.1.4
* 电脑系统：Windows 10 64位

如果你还没有搭建好开发环境，请到[这篇博客](http://www.aobosir.com/blog/2016/11/26/python3-large-web-crawler-001-Build-development-environment/)。


----------

所有的设置都是在scrapy爬虫项目中的`settings.py` 文件中进行设置。

**Step 1 . ** 设置爬虫不遵循 `robots.txt`协议

```
# Obey robots.txt rules
ROBOTSTXT_OBEY = False
```

![Alt text](/images/2016-12-6-python3-large-web-crawler-scrapy-project-Anti-reptile-settings/1480952600971.png)


> 想要了解什么是`robots.txt`协议，请访问这篇博客：[解析 robots.txt 文件](http://blog.csdn.net/github_35160620/article/details/52586126)。

**Step 2 . ** 设置取消**Cookies**

```python
# Disable cookies (enabled by default)
COOKIES_ENABLED = False
```

![Alt text](/images/2016-12-6-python3-large-web-crawler-scrapy-project-Anti-reptile-settings/1480952959564.png)


> **Cookies**：
>  
>  简单的说，Cookie就是服务器暂存放在你计算机上的一笔资料，好让服务器用来辨认你的计算机。当你在浏览网站的时候，Web服务器会先送一小小资料放在你的计算机上，Cookie 会帮你在网站上所打的文字或是一些选择，都记录下来。当下次你再光临同一个网站，Web服务器会先看看有没有它上次留下的Cookie资料，有的话，就会依据Cookie里的内容来判断使用者，送出特定的网页内容给你。 


**Step 3 . ** 设置用户代理值（`USER_AGENT`）

```python
# Crawl responsibly by identifying yourself (and your website) on the user-agent
USER_AGENT = 'Mozilla/xxx (Windows xxx; Winxx; xxx) AppleWebKit/xxx (KHTML, like Gecko) Chrome/xxxx Safari/xxx'
```

![Alt text](/images/2016-12-6-python3-large-web-crawler-scrapy-project-Anti-reptile-settings/1480953048379.png)

这个 用户代理可以在浏览器里面找到：

随便浏览一个网页，按**F12** -> **Network** -> **F5**，随便点击一项，你都能看到有 **User-agent** 这一项，将这里面的内容拷贝就可以。

![Alt text](/images/2016-12-6-python3-large-web-crawler-scrapy-project-Anti-reptile-settings/1480953359818.png)


**Step 4 . ** 设置IP 

对于这一步，如果你没有做什么违法的事情，可以不用设置。仅仅上面的三个步骤，就可以将那些具有反爬虫机制的网站可以正常爬取了。

