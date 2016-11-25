---
layout: post
title: "Python --- Scrapy 命令"
date: 2016-11-26 06:39:53 +0800
comments: true
sharing: true
categories: [Python3 大型网络爬虫实战]
tags: [python ,scrapy]
---

---

Scrapy 命令 分为两种：**全局命令** 和 **项目命令**。

全局命令：在哪里都能使用。

项目命令：必须在爬虫项目里面才能使用。

## 全局命令

```
C:\Users\AOBO>scrapy -h
Scrapy 1.2.1 - no active project

Usage:
  scrapy <command> [options] [args]

Available commands:
  bench         Run quick benchmark test
  commands
  fetch         Fetch a URL using the Scrapy downloader
  genspider     Generate new spider using pre-defined templates
  runspider     Run a self-contained spider (without creating a project)
  settings      Get settings values
  shell         Interactive scraping console
  startproject  Create new project
  version       Print Scrapy version
  view          Open URL in browser, as seen by Scrapy

  [ more ]      More commands available when run from project directory

Use "scrapy <command> -h" to see more info about a command
```

* **startproject**：创建一个爬虫项目：`scrapy startproject demo`（`demo` 创建的爬虫项目的名字）
* **runspider** 运用单独一个爬虫文件：`scrapy runspider abc.py`
* **veiw** 下载一个网页的源代码，并在默认的文本编辑器中打开这个源代码：`scrapy view http://www.aobossir.com/`
* **shell** 进入交互终端，用于爬虫的调试（如果你不调试，那么就不常用）：`scrapy shell http://www.baidu.com --nolog`（`--nolog` 不显示日志信息）
* **version** 查看版本：（`scrapy version`）
* **bench** 测试本地硬件性能（工作原理：）：`scrapy bench` （如果遇到问题：解决问题:  `import win32api ImportError: DLL load failed`，到[这里](http://www.aobosir.com/blog/2016/11/26/solve-pywin32-import-win32api-ImportError-DLL-load-failed/)查看解决办法。）

---

## 项目命令

（进入项目路径，才能看到项目命令）

```
D:\BaiduYunDownload\first>scrapy -h
Scrapy 1.2.1 - project: first

Usage:
  scrapy <command> [options] [args]

Available commands:
  bench         Run quick benchmark test
  check         Check spider contracts
  commands
  crawl         Run a spider
  edit          Edit spider
  fetch         Fetch a URL using the Scrapy downloader
  genspider     Generate new spider using pre-defined templates
  list          List available spiders
  parse         Parse URL (using its spider) and print the results
  runspider     Run a self-contained spider (without creating a project)
  settings      Get settings values
  shell         Interactive scraping console
  startproject  Create new project
  version       Print Scrapy version
  view          Open URL in browser, as seen by Scrapy

Use "scrapy <command> -h" to see more info about a command

D:\BaiduYunDownload\first>
```



* **genspider** 创建一个爬虫文件，我们在爬虫项目里面才能创建爬虫文件（这个命令用的非常多）（**startproject**：创建一个爬虫项目）。创建爬虫文件是按照以下模板来创建的，使用`scrapy genspider -l` 命令查看有哪些模板。

```
D:\BaiduYunDownload\first>scrapy genspider -l
Available templates:
  basic
  crawl
  csvfeed
  xmlfeed

D:\BaiduYunDownload\first>
```

> `basic` 基础
> `crawl`自动爬虫
> `csvfeed`用来处理csv文件
> `xmlfeed`用来处理xml文件
>  
> 按照`basic`模板创建一个名为`f1`的爬虫文件：`scrapy genspider -t basic f1` ，创建了一个`f1.py`文件。

* **check** 测试爬虫文件、或者说：检测一个爬虫，如果结果是：OK，那么说明结果没有问题。：`scrapy check f1`

* **crawl** 运行一个爬虫文件。：`scrapy crawl f1` 或者 `scrapy crawl f1 --nolog`

* **list** 列出当前爬虫项目下所有的爬虫文件： `scrapy list`

* **edit** 使用编辑器打开爬虫文件 （Windows上似乎有问题，Linux上没有问题）：`scrapy edit f1`

---
