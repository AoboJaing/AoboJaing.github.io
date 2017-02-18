---
layout: post
title: "Windows 上 使用CMake-GUI 软件生成 zlib 和 png 库的编译文件，然后使用VS2010编译"
date: 2017-02-11 08:08:16 +0800
comments: true
sharing: true
categories: [CMake-GUI]
tags: [PCL, CMake-GUI, zlib, png, vs2010, 编译第三方库]
---


----------

当我在编译Windows 上编译 PCL源代码的时候，它zlib库和png库的依赖，但是现在我的电脑里面并没有两个库。所以，我们现在就来手动的下载这两个库的源代码，然后亲自编译它们。


----------



参考网站：http://www.voidcn.com/blog/glunoy/article/p-6019106.html

我现在知道了。png库是依赖于zlib库的。（所以我们需要先编译zlib库）


现在我们电脑里面已经有zlib库了（我也不知道这个库是正有还是假有。不过当我们下面使用CMake-GUI软件生成png库的时候，CMake-GUI软件自动的天添加了zlib库的include文件的路径。所以，现在，我们就姑且认为当前的电脑立里面已经存在zlib库了。（但是我们继续后面的步骤发现，其实电脑里面并没有zlib库。）），但是没有png库，我们现在需要下载源码并编译：

到这里png库官网下载：http://libpng.sourceforge.net/index.html


![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486733756039.png)


下载 `libpng16`库：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486733871091.png)

下载，人下载最多的那个：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486733985739.png)

接着是：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734040450.png)

下载后解压。

然后使用CMake-GUI软件生成编译文件：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734198117.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734205651.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734211664.png)

出现一个错误：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734240388.png)

错误的原因就是没有找到`ZLIB`库的链接文件：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734281258.png)

手动添加，这个两个（Debug 和 Release）都填写同一个文件：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734344171.png)

现在再点击 **Configure** 按钮。

没有错误了。但是现在有红色的条目：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734380225.png)

现在再点击一次 `Configure` 按钮。红色条目消失：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734519705.png)


现在点击 **Generate** 按钮生成编译文件：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734548317.png)


----------

现在开始使用VS2010软件编译：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734582464.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734726006.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486734698502.png)

看来现在不行啊，我需要先下载并编译`zlib`库，然后在下载并编译`png`库。这才是正确的步骤。


----------

我们现在下载并编译zlib库：

下载zlib库源代码：

下载：https://sourceforge.net/projects/libpng/files/

依次的步骤是：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735206889.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735242472.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735278358.png)

下载完成后，我使用7-zip软件对其进行了两次解压。

然后使用CMake-GUI软件给它生产编译文件：


![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735448018.png)

点击 **Configure**按钮进行配置：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735463109.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735469279.png)

没有出现错误，出现了红色的条目：

我们现在来仔细的看看**INSTALL**条目：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735527480.png)

默认的添加的路径都是`C:\Program Files (x86)`。我们不能使用这个安装路径，原因是当我们一会在使用VS2010软件编译生成的编译文件的时候，会出现错误的，错误的原因是：没有权限。所以，我需要将这部分INSTALL条目的路径都修改为我们有权限的路径。

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735689013.png)

然后在点击 **COnfigure** 按钮。红色条目消失。

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735739401.png)


然后在点击 **Generate** 按钮。

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735744957.png)


----------

现在使用VS2010软甲打开刚刚生成的`.sln`文件：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735790730.png)

生成：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735812669.png)

很快，不到1秒钟就编译完成了：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735840702.png)

然后对 **INSTALL**项目进行**生成**

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735888551.png)

也是秒速编译完成：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735908123.png)


生成成功：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486735924463.png)


现在，我们将这个生成的文件夹，剪切到`C:\third_packages`路径里面。（我自己的一个习惯，我喜欢将第三方库放在这个路径下。）

我们还需要将zlib库的png路径添加到系统的环境变量里面。

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736460782.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736449182.png)

----------

现在我们可以将下面这两个文件夹给删除了。（一个是zlib的源代码。一个是zlib的编译文件）（当然，我们删除这两个文件夹之前，需要先关闭VS2010软件，因为刚刚VS2010软件一直在使用其中一个文件。CMake-GUI软件可以不用关闭，它不影响。）

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736039738.png)


----------

接下来，我们来编译 png库：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736190279.png)

修改zlib库（png库依赖于这个库）条目为正确的路径：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736285036.png)

现在点击 **Configure** 按钮。

红色的条目都消失了。现在有用一个点：我们需要注意这个安装路径：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736543109.png)

和zlib库是一样，我们需要给这个安装路径修改为一个我们可以控制的权限的路径。

修改为：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736593446.png)

现在点击 **Configure** 按钮，然后在点击 **Generate** 按钮：搞定


![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736628850.png)


----------

现在使用VS2010软件对生成的编译文件进行编译：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736678641.png)

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736696702.png)

编译成功，一共没有用了3秒钟：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736728357.png)


----------

然后是编译 **INSTALL**项目：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736754817.png)

秒速编译完成：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736783846.png)

一样，我们将得到的文件夹剪切到 `C:\third_packages`这个路径里面。

然后将`png`路径添加到环境变量里面：

![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736889900.png)


![Alt text](/images/2017-2-11-Compile-zlib-and-png-using-CMake-GUI-and-VS2010/1486736877915.png)


----------

最后一步就是清理战场：删除下面两个文件夹：（清理前，需要先关闭VS2010软件）


----------

好的，这样，zlib 和 png 这两个库就编译完成了。

## 搞定
