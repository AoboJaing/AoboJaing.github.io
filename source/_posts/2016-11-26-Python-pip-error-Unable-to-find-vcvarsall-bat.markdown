---
layout: post
title: "Python3 pip 解决问题：  error: Unable to find vcvarsall.bat"
date: 2016-11-26 05:50:14 +0800
comments: true
sharing: true
categories: [Python3 大型网络爬虫实战]
tags: [Visual Studio 2015, Windows, VS2015,error, pip, python3, vcvarsall.bat]
---



---

当我给 **python3.5** 安装 第三方库 `charset` 时：`pip install charset`，出现了错误：

![Alt text](/images/2016-11-26-Python-pip-error-Unable-to-find-vcvarsall-bat/1480092727015.png)

```
D:\WorkSpace\python_ws\python-large-web-crawler\firstdemo>pip install charset
Collecting charset
  Downloading charset-1.0.1.tar.gz (189kB)
    100% |████████████████████████████████| 194kB 3.9kB/s
Collecting chardet (from charset)
  Using cached chardet-2.3.0.tar.gz
Installing collected packages: chardet, charset
  Running setup.py install for chardet ... done
  Running setup.py install for charset ... error
    Complete output from command c:\users\aobo\appdata\local\programs\python\python35\python.exe -u -c "import setuptools, tokenize;__file__='C:\\Users\\AOBO\\AppData\\Local\\Temp\\pip-build-ydv8oep3\\charset\\setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record C:\Users\AOBO\AppData\Local\Temp\pip-hlxpja30-record\install-record.txt --single-version-externally-managed --compile:
    running install
    running build
    running build_py
    creating build
    creating build\lib.win-amd64-3.5
    creating build\lib.win-amd64-3.5\charset
    copying charset\cmd.py -> build\lib.win-amd64-3.5\charset
    copying charset\__init__.py -> build\lib.win-amd64-3.5\charset
    running egg_info
    writing charset.egg-info\PKG-INFO
    writing top-level names to charset.egg-info\top_level.txt
    writing dependency_links to charset.egg-info\dependency_links.txt
    writing requirements to charset.egg-info\requires.txt
    writing entry points to charset.egg-info\entry_points.txt
    warning: manifest_maker: standard file '-c' not found

    reading manifest file 'charset.egg-info\SOURCES.txt'
    reading manifest template 'MANIFEST.in'
    warning: no files found matching '*.txt' under directory 'docs'
    warning: no files found matching '*.txt' under directory 'languagedet\data'
    warning: no files found matching '*.pickle' under directory 'languagedet\data'
    warning: no files found matching '*.conf' under directory 'languagedet\data'
    writing manifest file 'charset.egg-info\SOURCES.txt'
    running build_ext
    building 'charset.detector' extension
    error: Unable to find vcvarsall.bat

    ----------------------------------------
Command "c:\users\aobo\appdata\local\programs\python\python35\python.exe -u -c "import setuptools, tokenize;__file__='C:\\Users\\AOBO\\AppData\\Local\\Temp\\pip-build-ydv8oep3\\charset\\setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" install --record C:\Users\AOBO\AppData\Local\Temp\pip-hlxpja30-record\install-record.txt --single-version-externally-managed --compile" failed with error code 1 in C:\Users\AOBO\AppData\Local\Temp\pip-build-ydv8oep3\charset\
```


---

## 为什么出现这个问题？ 

在命令行中执行：python，看看当前使用的python的版本，和它所需要的Vs软件的编译器的版本：

![Alt text](/images/2016-11-26-Python-pip-error-Unable-to-find-vcvarsall-bat/1480095090271.png)

当前python版本是：python3.5.0；当前需要的Vs编译器的版本是：MSC v. 1900

查看下面的表格，对于版本的Visual C ++使用的编译器版本如下：（[表的参考网站](http://stackoverflow.com/questions/2676763/what-version-of-visual-studio-is-python-on-my-computer-compiled-with)）

| Visual C ++版本 |     编译器版本|
| :-------- | --------:|
| Visual C++ 4.x |   MSC_VER=1000 |
|Visual C++ 5                   | MSC_VER=1100|
|Visual C++ 6                   | MSC_VER=1200|
|Visual C++ .NET               |  MSC_VER=1300|
|Visual C++ .NET 2003         |   MSC_VER=1310|
|Visual C++ 2005  (8.0)      |    MSC_VER=1400|
|Visual C++ 2008  (9.0)     |     MSC_VER=1500|
|Visual C++ 2010 (10.0)    |      MSC_VER=1600|
|Visual C++ 2012 (11.0)   |       MSC_VER=1700|
|Visual C++ 2013 (12.0)  |        MSC_VER=1800|
|Visual C++ 2015 (14.0) |         MSC_VER=1900|


所以解决这个 `error: Unable to find vcvarsall.bat` 问题的方法就是：下载并安装 Visual Studio 2015 软件，问题即可解决。

## 解决办法 --- 安装：**Python Tools 2.2.5 for Visual Studio 2015** 

**Step 1 . ** 下载 Visual Studio 2015 软件。

下载和安装 Visual Studio 2015 软件 的详细步骤请到这个博客查看：[下载和安装 Visual Studio 2015 软件 的详细步骤图文教程](http://www.aobosir.com/blog/2016/11/26/download-install-Miarosoft-Visual-Studio-2015-software-tutorial/)。（**我们按照这个网站的方法安装VS2015，但不按照这个博客里面说的安装。**）

> 如果安装上面的网站的方法安装VS2015软件，那么问题还是不能解决。（` error: Unable to find vcvarsall.bat`）

**Step 2 . ** 安装 Visual Studio 2015 软件

这个VS2015，安装时需要选择：**自定义安装**。（[参考网站](http://jingyan.baidu.com/article/adc815138162e8f723bf7387.html)）

参考网站：

![Alt text](/images/2016-11-26-Python-pip-error-Unable-to-find-vcvarsall-bat/1480108534366.png)

![Alt text](/images/2016-11-26-Python-pip-error-Unable-to-find-vcvarsall-bat/1480108637845.png)

我们的目的就是安装这个软件：**Python Tools 2.2.5 for Visual Studio 2015** 。现在，这个软件已经安装完了。

![Alt text](/images/2016-11-26-Python-pip-error-Unable-to-find-vcvarsall-bat/1480109167911.png)

> **注意：**
>  
>  如果一直停留在：“正在配置您的系统，这可能需要一些时间”
>   
>  ![Alt text](/images/2016-11-26-Python-pip-error-Unable-to-find-vcvarsall-bat/1480109561343.png)
>   
>   解决：关掉VS的所有进程。


## 搞定，问题解决

---

现在再执行：`pip install charset`。问题解决。

![Alt text](/images/2016-11-26-Python-pip-error-Unable-to-find-vcvarsall-bat/1480109745990.png)


----------

