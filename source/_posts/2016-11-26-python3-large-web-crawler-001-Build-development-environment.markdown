---
layout: post
title: "Python3 大型网络爬虫实战 001 --- 搭建开发环境"
date: 2016-11-26 06:28:27 +0800
comments: true
sharing: true
categories: [Python3 大型网络爬虫实战]
tags: [Visual Studio 2015, Windows, VS2015, python3 ,pip ,Twisted、pywin32、scrapy, lxml]
---


---

我使用的电脑： Windows 10 64位

## 前言

开发Python爬虫有很多种方式，从程序的复杂程度的角度来说，可以分为：爬虫项目和爬虫文件。
相信有些朋友玩过Python的urllib模块，一般我们可以用该模块写一些爬虫文件，实现起来非常方便，但做大型项目的时候，会发现效率不是太好、并且程序的稳定性也不是太好。
Scrapy是一个Python的爬虫框架，使用Scrapy可以提高开发效率，并且非常适合做一些中大型爬虫项目。
简单来说，urllib库更适合写爬虫文件，scrapy更适合做爬虫项目。

本套专栏，就来讲解如何做爬虫项目。本篇博客是第一篇博客：搭建开发环境。


## 1 . 安装Python3

到官网下载就可以了，下载一个Python3.5版本就可以，傻瓜式安装。

> Python 3 被默认安装在：`C:\Users\[Username]\AppData\Local\Programs\Python\Python35` 这个路径里面。

## 2 . 安装Python程序开发集成开发环境 --- PyCharm IDE 2016.1.4

软件下载：https://www.jetbrains.com/pycharm/download/#section=windows

注意：

Professional是完整版的，但是需要注册码

注册方法：http://blog.csdn.net/tianzhaixing2013/article/details/44997881

我这次安装的是PyCharm 2016。


> Community是免费版的，但是软件里面的Terminal是不能使用的。

## 3 . 安装 Visual Studio 2015 软件

要知道：为什么需要 Visual Studio 软件了。（参考[这个网站](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/)）

如果不安装，当中你执行`pip install third-package-name`时，有时会出现下面这个错误：`  error: Unable to find vcvarsall.bat`

![Alt text](/images/2016-11-26-python3-large-web-crawler-001-Build-development-environment/1480104934562.png)

安装Visual Studio 2015 软件是为了安装里面的**Python Tools 2.2.5 for Visual Studio 2015**软件。

**下载和安装 Visual Studio 2015 软件 的方法在**[**这里**](http://www.aobosir.com/blog/2016/11/26/Python-pip-error-Unable-to-find-vcvarsall-bat/)。

## 4 . 升级 pip 工具

在DOS窗口中执行下面的命令来升级pip工具。

```
python -m pip install --upgrade pip
```

## 5 . 安装一些第三方库

lxml、Twisted、pywin32、scrapy

lxml是一种可以迅速、灵活地处理 XML。
Twisted是用Python实现的基于事件驱动的网络引擎框架。
pywin32提供win32api。
Scrapy是一个为了爬取网站数据，提取结构性数据而编写的应用框架。

---

我们安装的是python3.5，并且我的电脑是64位的，所以：下载：

lxml‑3.6.4‑cp35‑cp35m‑win_amd64.whl

Twisted‑16.5.0‑cp35‑cp35m‑win_amd64.whl

pywin32‑220.1‑cp35‑cp35m‑win_amd64.whl

scrapy(直接使用命令：`pip.exe install scrapy` 来安装。)

---

Python安装第三方库的方法：http://blog.csdn.net/github_35160620/article/details/52203682

> 注意：如果你的电脑之前安装了Python2，那么Python2 有自己的pip工具，Python3 也是有自己的pip工具，所以，如果你在DOS命令行上执行`pip install some-package-name`命令的时候，系统会使用哪个pip工具呢？是python2的pip，还是python3的pip？
>  
> 这个问题，你可以在这篇博客里得到解决答案：http://www.aobosir.com/blog/2016/11/23/pip-install-python2-python3/


---

下载后，在我的电脑上是这样安装：

安装 lxml：

```
C:\Users\AOBO>cd C:\Users\AOBO\AppData\Local\Programs\Python\Python35\Scripts
C:\Users\AOBO\AppData\Local\Programs\Python\Python35\Scripts>pip.exe install D:\software_install_package_win\python\some-Python-third-packages\lxml-3.6.4-cp35-cp35m-win_amd64.whl
Processing d:\software_install_package_win\python\some-python-third-packages\lxml-3.6.4-cp35-cp35m-win_amd64.whl
Installing collected packages: lxml
Successfully installed lxml-3.6.4

```

安装 Twisted ：（执行到`Collecting constantly>=15.1 (from Twisted==16.5.0)`这句时，卡住了，我按了 Ctrl+C 才继续执行下去。自动下载了下面的：constantly、incremental、zope.interface 这三个依赖库）

```
C:\Users\AOBO\AppData\Local\Programs\Python\Python35\Scripts>pip.exe install D:\software_install_package_win\python\some-Python-third-packages\Twisted-16.5.0-cp35-cp35m-win_amd64.whl
Processing d:\software_install_package_win\python\some-python-third-packages\twisted-16.5.0-cp35-cp35m-win_amd64.whl
Collecting constantly>=15.1 (from Twisted==16.5.0)
#(执行到这卡住了，我按了 Ctrl+C 才继续执行下去。自动下载了下面的：constantly、incremental、zope.interface 这三个依赖库)
  Downloading constantly-15.1.0-py2.py3-none-any.whl
Collecting incremental>=16.10.1 (from Twisted==16.5.0)
  Downloading incremental-16.10.1-py2.py3-none-any.whl
Collecting zope.interface>=4.0.2 (from Twisted==16.5.0)
  Downloading zope.interface-4.3.2-cp35-cp35m-win_amd64.whl (136kB)
    100% |████████████████████████████████| 143kB 7.1kB/s
Requirement already satisfied: setuptools in c:\users\aobo\appdata\local\programs\python\python35\lib\site-packages (from zope.interface>=4.0.2->Twisted==16.5.0)
Installing collected packages: constantly, incremental, zope.interface, Twisted
Successfully installed Twisted-16.5.0 constantly-15.1.0 incremental-16.10.1 zope.interface-4.3.2
```

安装pywin32：

```
C:\Users\AOBO\AppData\Local\Programs\Python\Python35\Scripts>pip.exe install D:\software_install_package_win\python\some-Python-third-packages\pywin32-220.1-cp35-cp35m-win_amd64.whl
Processing d:\software_install_package_win\python\some-python-third-packages\pywin32-220.1-cp35-cp35m-win_amd64.whl
Installing collected packages: pywin32
Successfully installed pywin32-220.1
```

安装scropy：

```
C:\Users\AOBO\AppData\Local\Programs\Python\Python35\Scripts>pip.exe install scrapy
Collecting scrapy
  Downloading Scrapy-1.2.1-py2.py3-none-any.whl (294kB)
    100% |████████████████████████████████| 296kB 338kB/s
Collecting service-identity (from scrapy)
  Downloading service_identity-16.0.0-py2.py3-none-any.whl
Collecting six>=1.5.2 (from scrapy)
  Downloading six-1.10.0-py2.py3-none-any.whl
Collecting w3lib>=1.15.0 (from scrapy)
  Downloading w3lib-1.16.0-py2.py3-none-any.whl
Collecting PyDispatcher>=2.0.5 (from scrapy)
  Downloading PyDispatcher-2.0.5.tar.gz
Requirement already satisfied: Twisted>=10.0.0 in c:\users\aobo\appdata\local\programs\python\python35\lib\site-packages (from scrapy)
Requirement already satisfied: lxml in c:\users\aobo\appdata\local\programs\python\python35\lib\site-packages (from scrapy)
Collecting cssselect>=0.9 (from scrapy)
  Downloading cssselect-1.0.0-py2.py3-none-any.whl
Collecting parsel>=0.9.3 (from scrapy)
  Downloading parsel-1.1.0-py2.py3-none-any.whl
Collecting queuelib (from scrapy)
  Downloading queuelib-1.4.2-py2.py3-none-any.whl
Collecting pyOpenSSL (from scrapy)
  Downloading pyOpenSSL-16.2.0-py2.py3-none-any.whl (43kB)
    100% |████████████████████████████████| 51kB 4.7MB/s
Collecting pyasn1 (from service-identity->scrapy)
  Downloading pyasn1-0.1.9-py2.py3-none-any.whl
Collecting pyasn1-modules (from service-identity->scrapy)
  Downloading pyasn1_modules-0.0.8-py2.py3-none-any.whl
Collecting attrs (from service-identity->scrapy)
  Downloading attrs-16.2.0-py2.py3-none-any.whl
Requirement already satisfied: constantly>=15.1 in c:\users\aobo\appdata\local\programs\python\python35\lib\site-packages (from Twisted>=10.0.0->scrapy)
Requirement already satisfied: zope.interface>=4.0.2 in c:\users\aobo\appdata\local\programs\python\python35\lib\site-packages (from Twisted>=10.0.0->scrapy)
Requirement already satisfied: incremental>=16.10.1 in c:\users\aobo\appdata\local\programs\python\python35\lib\site-packages (from Twisted>=10.0.0->scrapy)
Collecting cryptography>=1.3.4 (from pyOpenSSL->scrapy)
  Downloading cryptography-1.6-cp35-cp35m-win_amd64.whl (1.3MB)
    100% |████████████████████████████████| 1.3MB 257kB/s
Requirement already satisfied: setuptools in c:\users\aobo\appdata\local\programs\python\python35\lib\site-packages (from zope.interface>=4.0.2->Twisted>=10.0.0->scrapy)
Collecting cffi>=1.4.1 (from cryptography>=1.3.4->pyOpenSSL->scrapy)
  Downloading cffi-1.9.1-cp35-cp35m-win_amd64.whl (158kB)
    100% |████████████████████████████████| 163kB 322kB/s
Collecting idna>=2.0 (from cryptography>=1.3.4->pyOpenSSL->scrapy)
  Downloading idna-2.1-py2.py3-none-any.whl (54kB)
    100% |████████████████████████████████| 61kB 4.4MB/s
Collecting pycparser (from cffi>=1.4.1->cryptography>=1.3.4->pyOpenSSL->scrapy)
  Downloading pycparser-2.17.tar.gz (231kB)
    100% |████████████████████████████████| 235kB 311kB/s
Installing collected packages: six, pycparser, cffi, pyasn1, idna, cryptography, pyOpenSSL, pyasn1-modules, attrs, service-identity, w3lib, PyDispatcher, cssselect, parsel, queuelib, scrapy
  Running setup.py install for pycparser ... done
  Running setup.py install for PyDispatcher ... done
Successfully installed PyDispatcher-2.0.5 attrs-16.2.0 cffi-1.9.1 cryptography-1.6 cssselect-1.0.0 idna-2.1 parsel-1.1.0 pyOpenSSL-16.2.0 pyasn1-0.1.9 pyasn1-modules-0.0.8 pycparser-2.17 queuelib-1.4.2 scrapy-1.2.1 service-identity-16.0.0 six-1.10.0 w3lib-1.16.0
```

---

查看 `scrapy` 是否安装成功：（执行`scrapy -h` 命令，如果能输出信息，说明安装成功）

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

C:\Users\AOBO>

```

---

检查所有刚刚安装的库是否安装成功：

启动**PyCharm** 软件，新建一个工程：

![Alt text](/images/2016-11-26-python3-large-web-crawler-001-Build-development-environment/1479835108332.png)

![Alt text](/images/2016-11-26-python3-large-web-crawler-001-Build-development-environment/1479835159526.png)

刚刚安装的库在这里可以看到：

![Alt text](/images/2016-11-26-python3-large-web-crawler-001-Build-development-environment/1479840214905.png)

安装成功。

---

## 6 . 一个超好的命令行串口软件 --- PowerCmd

PowerCmd 是一款Windows CMD 的增强工具。

下载安装地址：http://www.aobosir.com/blog/2016/11/23/powercmd-install/

> 这个软件真的很喽，像我执行`scrapy -h` 这样的命令，都打印不出信息，在DOS窗口里面是有信息打印出来的。

---


---

## 测试环境

1 . 执行 `scrapy -h`，如果有打印出来信息，说明Scrapy  安装成功。

2 . 执行 `scrapy bench` ，如果遇到问题，说明pywin32库还有需要完成的步骤。（解决问题:  import win32api ImportError: DLL load failed，到这里查看解决办法。）


---

接下来，我们[学习 Scrapy 的命令](http://www.aobosir.com/blog/2016/11/26/python-Scrapy-command/)。了解了**Scrapy** 命令后，我学习：scrapy 爬虫项目的创建及爬虫的创建 --- 实例：爬取百度标题和CSDN博客。


---
