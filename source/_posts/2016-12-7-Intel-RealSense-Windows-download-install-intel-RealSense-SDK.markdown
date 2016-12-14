---
layout: post
title: "Intel RealSense 002(Learning RealSense SDK 001) Windows安装 Intel RealSense SDK"
date: 2016-12-07 12:18:38 +0800
comments: true
sharing: true
categories: [Learning Intel RealSense SDK]
tags: [Intel RealSense, Windows, SDK, 安装软件,SR300]
---


----------

我使用的Intel RealSense 硬件：SR300 摄像头

参考网站：

* [Downloading and Installing the Intel® RealSense SDK](https://www.youtube.com/watch?v=dFVUiwyWyFo&list=PLg-UKERBljNwbHO7R9t0mnIA52xd65LUT&index=6)
* [Getting Started with Intel® RealSense™ App Development: Step-by-Step Install Instructions](https://software.intel.com/blogs/2015/09/13/detailed-instructions-for-getting-started-with-intel-realsense-app-development?utm_source=ISTV&utm_medium=Video&utm_campaign=ISTV_2016&utm_content=Video)

## [下载](https://software.intel.com/zh-cn/intel-realsense-sdk/download) 并安装

**Step 0 . ** 先将SR300摄像头通过USB3.0接口插到电脑上。

> 注意：
>  
> 1. 必须要将SR300摄像头连接到USB3.0接口上。（这是一个非常重要的步骤）
> 2. 不要通过USB延长线连接。


![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481009695299.png)

等待大约5分钟，驱动就自动安装完成了。

![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481009996712.png)

> 如果电脑没有帮你自动安装，你需要手动安装：**Step 1**。电脑帮你自动安装了SR300 摄像头的驱动程序，你就可以跳过**Step 1**。


**Step 1 . ** 下载[SR300 深度摄像头管理程序](https://software.intel.com/zh-cn/intel-realsense-sdk/download)（intel_rs_dcm_sr300_3.3.27.5718.exe）

> **DCM** 是全称：Depth Camera Manager

安装：按照提示，一步一步的进行操作即可。

> 如果你需要这个问题：
> 
> ![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481008202698.png)
>  
> 说明：SR300 摄像头没有与电脑连接，请先将SR300 摄像头于电脑通过USB3.0接口连接。

**Step 2 . ** 下载 [英特尔® 实感™ 软件开发套件（必备）](https://software.intel.com/zh-cn/intel-realsense-sdk/download)（Intel® RealSense™ SDK for Windows*）

> 下载这里，你需要先注册一个inteld的用户，才能下载它。

安装：intel_rs_sdk_offline_package_10.0.26.0396.exe

一步一步的安装，即可。


> 如果你在安装的时候遇到这个问题：
>  
> ![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481021331695.png)
> 
> **The Installer failed to detect OpenCL™ 1.2 support on your system. Certain SDK samples/modules may not be functional. Please upgrade your graphics driver for full SDK functionalities.**
> 
> 点击**Next** 按钮忽略即可。
> 
> ## 出现这个问题的原因：
>  
> 你先下载 [GPU Caps Viewer](http://www.ozone3d.net/gpu_caps_viewer/) 软件来查看**我当前的电脑安装的OpenCL的版本**和**我的电脑有没有GPU**。
>  
>  
> ![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481048947084.png)
> 
>![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481048958442.png) ![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481049035444.png)
> 
> 通过GPU Caps Viewer软件得到的结果，我知道了：
> 
> * 我的电脑里面是有GPU的：(NVIDIA CUDA公司的)[GeForce GT 705](http://www.geforce.com/hardware/notebook-gpus/geforce-705m/specifications)。
> * 这个显卡（GPU）支持的OpenCL版本是1.1
> 
> 现在你应该大概知道了：安装的 Intel RealSense SDK 提示的安装问题的原因了吧：
> 
>![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481049133289.png)
> 
> 它说：您当前电脑的显卡太喽了，Intel RealSense SDK需要的是OpenCL1.2，而你的电脑里面没有，你电脑里面的显卡所支持的OpenCL版本是OpenCL1.1。
>  
> ## 解决办法
>  
> 没有办法，唯一可以解决下面这个问题的办法就是：提升（换一个好的）图形驱动硬件。（即：支持OpenCL1.2以上的显卡）。我们直接直接忽略这个问题也可以。对后面基本没有什么影响。
> 


----------


> **总结：** 对于你的电脑，你想检测是否有GPU（显卡）（不管是**NVIDIA CUDA 公司**的还是 **Intel公司**的 都可以）。然后查看GPU（显卡）支持的OpenCL版本，必须要大于等于OpenCL1.2，否则 Intel RealSense SDK 安装不能成功。


----------

注意安装的时候要连着网，因为在安装的时候会从网上下载一下安装包。

![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481072982805.png)

如果你想要拥有 **China** 的语音识别和合成包，可以将下面的选项勾选。

![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481073189997.png)


----------

## 搞定

## 测试

启动 **Intel RealSense SDK Sample Browser** 

![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481083199264.png)

里面有很多的示例可以运行：（每个程序都运行一下，试试看。）

![Alt text](/images/2016-12-7-Intel-RealSense-Windows-download-install-intel-RealSense-SDK/1481083256629.png)


----------

学习文档：[英特尔® 实感™ SDK 文档](https://software.intel.com/zh-cn/intel-realsense-sdk/documentation)
