---
layout: post
title: "ROS Learning-033  （提高篇-011 URDF）如何使用SolidWorks软件导出URDF机器人模型文件   — 00 给SolidWorks软件安装 sw_urdf_exporter插件"
date: 2017-02-21 12:25:03 +0800
comments: true
sharing: true
categories: [ROS, sw_urdf_exporter]
tags: [ROS, SolidWorks, URDF, sw_urdf_exporter]
---


# ROS 提高篇 之 **使用SolidWorks软件导出URDF机器人模型文件** --- 00 给SolidWorks软件安装 **sw_urdf_exporter**插件 


---

* 我使用的虚拟机软件：**VMware Workstation 11**
* 使用的**Ubuntu**系统：**Ubuntu 14.04.4 LTS**
* **ROS** 版本：**ROS Indigo**
* 我使用的SolidWorks软件的版本： **SolidWorks 2011**
* 安装SolidWorks软件的电脑系统：Windows 10系统


## 前提条件：你需要先在你的电脑里面安装SolidWorks软件。SolidWorks软件的下载安装和破解的图文教程，你可以参考这篇博文：[Solidworks 2011软件下载，安装和破解图文教程](http://www.aobosir.com/blog/2017/02/19/download-install-crack-graphic-tutorial/)

---

**注意：**
1 . **ROS** 提高篇这个专栏的教学有门槛。
2 . 如果你没有学习前面的教程，请想学习前面的 **beginner_Tutorials** 和 **learning_tf** 的**ROS** 相关教程。
3 . 你还需要会使用SolidWorks软件。[这里](http://www.aobosir.com/tags/solidworks/)有相关的博文。

---


## **sw_urdf_exporter**

参考网站：[SolidWorks to URDF Exporter](http://wiki.ros.org/sw_urdf_exporter)

**sw_urdf_exporter**它使用一个SolidWorks软件的一个插件，这个插件是ROS团队设计的。**sw_urdf_exporter**这个插件的官方介绍网站在[这里](http://wiki.ros.org/sw_urdf_exporter)。

下面来简单的介绍一下这个插件：这个插件的功能是将SolidWorks里面的模型导出成URDF格式的文件，也就是说，我们其实可以管这个插件叫做：[SolidWorks](http://www.aobosir.com/blog/2017/02/19/download-install-crack-graphic-tutorial/)里面的URDF文件的导出器。这个导出器将会创建一个类似ROS的包，其中包的路径里面包含模型的网络（Mesh）、纹理（Texture）和机器人模型文件（URDF）文件。对于当个的SolidWorks模型文件，导出程序将在URDF文件里面创建单个链接；对于SolidWorks的装配件，导出程序江湖构建链接，然后在基于SolidWorks组件层次创建结构树，导出程序中的输出器可以自动确定正确的关节类型、关节变换和轴（joint type, joint transforms and axes）。


## 下载 **sw_urdf_exporter**

到[这个网站](http://wiki.ros.org/sw_urdf_exporter)里面，直接点击下面这个按钮：

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487623172541.png)

当弹出一个网页，点击里面的 **View raw**，就可以下载了：

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487623229944.png)

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487623272693.png)


----------

下载后，双击运行。（我现在先不急着运行，我们先说说使用这个软件的注意事项，然后在手把手的给你介绍如何给[SolidWorks](http://www.aobosir.com/blog/2017/02/19/download-install-crack-graphic-tutorial/)软件安装这个插件。）


----------


## 对于这个插件，使用时，需要注意几点

* 这个插件在SolidWorks 2012 版本里面可以正常的使用，但是对于更高的版本不知道兼容性如何。
* 如果你想要获取SolidWorks ROS这个插件最新的通知，你可以在这个网页里面获取到：[ROS SolidWorks SIG](https://groups.google.com/forum/?fromgroups#!forum/ros-sig-solidworks)
* 这个插件不依赖于ROS系统，也就是说，我们可以在我们的安装了[SolidWorks](http://www.aobosir.com/blog/2017/02/19/download-install-crack-graphic-tutorial/)软件的Windows 10电脑上，将SolidWorks里面的模型文件通过这个插件将其导出成[URDF](http://wiki.ros.org/urdf)文件。然后再给别的Ubuntu系统使用。（可以将任何SolidWorks模型文件导出成[URDF](http://wiki.ros.org/urdf)文件。）
* 这个插件目前只能运行在64位的Windows系统上，32位的系统不能运行。


## 安装

安装需要注意的事情：

* 你不能将其安装到标有`SW2URDF`的目录。否则运行程序会抛出未处理的异常错误。

* 同时，因为这个插件是使用**C#**编写的，所以，如果你的电脑里面安装`.NET Framework V4`，或者没有升级到`.NET Framework V4`以上，你需要先安装[这个](https://www.microsoft.com/zh-cn/download/details.aspx?id=17718)。

上面的两个注意事项的知道了后，我们现在就来安装。双击刚刚下载的安装包。


> 其实你也可以直接下载源代码，然后在使用Visual Studio 软件来手动编译生成可执行文件。
>  
> **sw_urdf_exporter**项目的源代码在这里下载：
>  
> 下载需要使用 `hg` 或者 `ssh` 命令来下载，`git`工具时不能下载**Bitbucket**这个网站里面的源代码的，又因为我的Windows系统电脑里面只安装了git工具，所以下面我介绍的下载方法是：直接下载源代码。
>  
>  点击 **Download** 标签：
>  
> ![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487626201507.png)
> 
> 然后直接点击 **Download repository** 就下载了。
>  
>  ![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487626279426.png)
>   
>  下载好了，解压，里面有**sw_urdf_exporter**项目的源代码，以及一些示例模型（SolidWorks模型）。


（我们这里是使用安装包进行安装。）双击安装包，它会自动的识别到你电脑里面当前安装了SolidWorks软件的路径。我们直接 **Next**。

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487628670908.png)

点击 **Intall**

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487628830450.png)

秒速完成。点击 **Finish**

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487628845674.png)


----------

好的，现在已经安装完成了。现在启动SolidWorks软件：

选择： **插件...**

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487629154657.png)


----------

你会在 **其他插件** 里面看到一项 `SW2URDF`，正确情况是被勾选的，如果没有被勾选，请勾选。

![Alt text](/images/2017-2-21-ROS-sw_urdf_exporter-download-install-and-add-plug-in-solidworks/1487629315046.png)

## 搞定

现在就已经想这个插件安装成功了。下面我们就来测试一下这个插件如何使用。


----------


## 使用这个插件

对于这个插件，ROS官方给出了专门的教程，在[这里](http://wiki.ros.org/sw_urdf_exporter/Tutorials)。


接下来，下一个博文，我们就来介绍，这个插件如何使用。

* [将SolidWorks零件导出为URDF文件](http://wiki.ros.org/sw_urdf_exporter/Tutorials/Export%20a%20Part)
* [将SolidWorks装配件导出为URDF文件](http://wiki.ros.org/sw_urdf_exporter/Tutorials/Export%20an%20Assembly)
* [简化大型装配件的SolidWorks和URDF导出程序工作流程](http://wiki.ros.org/sw_urdf_exporter/Tutorials/Organizing%20SolidWorks%20Assembly%20for%20URDF%20Exporter)

