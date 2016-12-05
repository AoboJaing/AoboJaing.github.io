---
layout: post
title: "Learning pcduino 002 给pcduino烧写系统 — 之 烧写Ubuntu 14系统"
date: 2016-12-05 22:19:23 +0800
comments: true
sharing: true
categories: [pcduino]
tags: [pcduino, pcduino3B, Ubuntu 14]
---


----------

* 我使用的pcduino板卡型号：[pcduino 3B](http://www.aobosir.com/blog/2016/12/05/pcduino-3B-Board-Introduction/)
* 我使用的TF卡大小：32G


----------

参考网站：

* [Installing Ubuntu 14 on a pcDuino3B](https://www.youtube.com/watch?v=XXauYnwElpQ)


----------


## 下载需要的东西

下载 系统镜像文件 和 必要的烧写工具。（我使用的下载软件是迅雷，不是浏览器自带的下载器）


以我现在使用的板子（pcduino3B）为例，所以在[这个网站](http://www.linksprite.com/image-for-pcduino3-nano-pcduino3b/)里面下载。需要现在三个东西：

1. 一个是系统镜像文件。
2. 一个烧写工具。

> 如果你使用的不是pcduino3B板子，那么请到 [这个网站](http://www.linksprite.com/pcduino-download/)里选择你使用的板子，到对应的板子链接里下载对应板子的内核镜像文件、系统镜像文件和必要的烧写工具。




**Step 1 . ** 下载镜像文件

镜像文件选择下面的 Ubuntu 14 下载：（注意，这个Ubuntu 14 只需要下载这个文件即可，因为它是一个 **内核+系统** 的镜像文件。）

![Alt text](/images/2016-12-5-pcduino-programming-system-ubuntu-14/1480946917168.png)

**Step 2 . ** 下载烧写工具

所以，我下载 **PhoenixCard** 烧写工具：（烧写工具在网页的下面，往下滚就能看到。）

![Alt text](/images/2016-12-5-pcduino-programming-system-ubuntu-14/1480947440669.png)

> 注意：注意它的下载提示。如果是给pcduino3系列使用，必须要使用 Phonenix card这个 软件的 V309 版本。很不错的是：这个下载链接默认下载的就是 Phonenix card V309。


----------

## 给pcduino板子烧写Ubuntu 14系统

**Step 1 . ** 用读卡器将TF卡（小型的SD卡）连接到电脑。（必须）使用**SD Formatter**工具（专业格式化SD卡的软件）对TF卡进行格式化。


> **SD Formatter**工具具体的下载、安装和使用，请到[这篇博客](http://blog.csdn.net/github_35160620/article/details/52038918)中进行了解。

**Step 2 . ** 烧写工具 **PhoenixCard** 下载完，解压后，直接双击**PhoenixCard.exe**就可以启动 **PhoenixCard**烧写软件。

点击**镜像文件**按钮，选择刚刚下载解压后的镜像文件。

然后点击 **烧录** 按钮，进行烧录。（大于5分钟时间。）

**Step 3 . ** 将TF卡插到pcduino板子上，只给板子供电即可。

> 注意：
>  
> * pcduino板子只需要插上TF卡和接通电源即可，其他的什么设备都不需要连接。
> * 接通电源一定要是5V2A，最好是使用充电宝或者充电头直接给板子供电。**不可以使用电脑USB接口给板子供电。因为电流不够。**
> * 如果你真的使用电脑的USB接口给板子供电，后面板子安装系统镜像的时候，是不会成功的。


![Alt text](/images/2016-12-5-pcduino-programming-system-ubuntu-14/1480947234663.png)


中间的LED4（TX）一1秒的间隔闪烁，说明正在烧写内核和系统程序（pcduino板子全自动烧写），大约不到3分钟左右，中间这个LED不再闪烁（熄灭），说明：内核和系统烧写完成。这时拔下TF卡，再将pcduino板子断开电源。

**Step 4 . ** 给pcduino板子连接显示器，再接通电源：（这时pcduino板子还不插TF卡）

Ubuntu 14系统成功运行。


## 搞定
