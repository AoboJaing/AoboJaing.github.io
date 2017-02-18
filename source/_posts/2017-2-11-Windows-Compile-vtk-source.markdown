---
layout: post
title: "Windows上手动编译VTK源代码"
date: 2017-02-11 08:25:21 +0800
comments: true
sharing: true
categories: [CMake-GUI]
tags: [Windows, VTK, CMake-GUI, VS2010, 第三方库编译]
---


----------



# 下载 VTK （7.1.0 版本）

下载网站：http://www.vtk.org/download/

下载下面这个：大约40多M

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486664521880.png)


----------

## 使用CMake-GUI软件生成编译文件

解压VTK。然后使用CMake-GUI软件，生成编译文件：



第一次点击 **Configure** 按钮，选择的编译器是：**Visual Studio 10 2010**（就是VS2010 软件 32位的），大约要执行3分多钟。

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486667440556.png)

出现了红色的条目。然后，在点击**Configure** 按钮一次。

不在有红色条目。

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486667504849.png)

点击**Generate** 按钮。

搞定：

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486667544319.png)


----------

## 开始编译VTK：

我们使用VS2010软件编译。使用VS2010软件打开下面的文件：

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486667661222.png)


点击生成：

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486667698053.png)


> VTK库是一个比较底层的库，它没有什么依赖库，所以编译VTK库是一件比较容易的事情。


执行了30多分钟，现在，全部编译成功：

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486669531270.png)


----------

然后我们在生成 **INSTALL**

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486670425630.png)


有一个执行失败：失败的原因是：需要管理员权限。

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486670387856.png)


----------

解决办法：（参考网站：[这里](http://public.kitware.com/pipermail/vtkusers/2010-August/061898.html)）

所以，我们现在关闭这个VS2010软件。打开CMake-GUI，重新生成编译文件：

我们将 **CMAKE_INSTALL_PREFIX** 条目设置为一个我们有权限新建文件的路径：

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671350467.png)

再次点击 **Configure** 按钮。

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671408818.png)

最后在点击 **Generates** 按钮。

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671440035.png)


----------

现在点击：**VTK.sln** 文件

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671467333.png)


----------

对着**ALL_BUILD** 右键，点击 **生成**

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671511547.png)

这次执行，也就5分钟左右。	

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671854513.png)

----------

现在，我们生成 **INSTALL** ：

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671928418.png)


![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486671904455.png)


----------

然后，我们再将这个文件夹剪切到`C:\Program Files (x86)` 路径里面：

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486672083636.png)

![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486672171677.png)

我们需要将`\bin\` 路径（`C:\Program Files (x86)\VTK\bin`）添加到环境变量里面。


![Alt text](/images/2017-2-11-Windows-Compile-vtk-source/1486672352228.png)


----------

## 搞定
