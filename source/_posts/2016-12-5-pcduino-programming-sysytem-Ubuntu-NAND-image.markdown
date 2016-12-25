---
layout: post
title: "Learning pcduino 001 给pcduino烧写系统 — 之 烧写Ubuntu NAND系统"
date: 2016-12-05 21:50:42 +0800
comments: true
sharing: true
categories: [pcduino]
tags: [pcduino, pcduino3B, Ubuntu NAND]
---


----------

* 我使用的pcduino板卡型号：[pcduino 3B](http://www.aobosir.com/blog/2016/12/05/pcduino-3B-Board-Introduction/)
* 我使用的TF卡大小：32G


----------

参考网站：

* [\[Video\] Run built-in Arduino IDE on pcDuino3](http://learn.linksprite.com/pcduino/quick-start/pcduino3/video-run-built-in-arduino-ide-on-pcduino3/)


## 下载需要的东西

下载 内核镜像文件、系统镜像文件 和 必要的烧写工具。（我使用的下载软件是迅雷，不是浏览器自带的下载器）


以我现在使用的板子（pcduino3B）为例，所以在[这个网站](http://www.linksprite.com/image-for-pcduino3-nano-pcduino3b/)里面下载。需要现在三个东西：

1. 一个内核文件镜像文件。
2. 一个是系统镜像文件。
3. 一个烧写工具。

> 如果你使用的不是pcduino3B板子，那么请到 [这个网站](http://www.linksprite.com/pcduino-download/)里选择你使用的板子，到对应的板子链接里下载对应板子的内核镜像文件、系统镜像文件和必要的烧写工具。


**Step 1 . ** 下载Kernel(内核)镜像文件

下面的4个都是同一个内核文件，随便点击一个下载即可。（这里面说的：**PhoenixCard** 就是烧写工具）

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480777105671.png)

> 注意：如果你给pcduino板子连接的是**LVDS Screen**显示屏，那么你需要下载的是上面图片中的**LVDS Screen**的**Kernel**内核文件。
>  
> ![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480938335315.png)


**Step 2 . ** 下载烧写工具

所以，我下载 **PhoenixCard** 烧写工具：（烧写工具在网页的下面，往下滚就能看到。）

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480744828441.png)

> 注意：注意它的下载提示。如果是给pcduino3系列使用，必须要使用 Phonenix card这个 软件的 V309 版本。很不错的是：这个下载链接默认下载的就是 Phonenix card V309。

**Step 3 . ** 下载镜像文件

镜像文件随便选择一个 Ubuntu NAND 下载即可：（注意，要对应上面下载的内核文件。）

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480938647531.png)


----------

## 给pcduino板子烧写内核

**Step 1 . ** 用读卡器将TF卡（小型的SD卡）连接到电脑。（必须）使用**SD Formatter**工具（专业格式化SD卡的软件）对TF卡进行格式化。

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480939221029.png)

> **SD Formatter**工具具体的下载、安装和使用，请到[这篇博客](http://blog.csdn.net/github_35160620/article/details/52038918)中进行了解。


**Step 2 . ** 烧写工具 **PhoenixCard** 下载完，解压后，直接双击**PhoenixCard.exe**就可以启动 **PhoenixCard**烧写软件：

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480745667635.png)

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480745770272.png)


**Step 3 . ** 给TF卡烧写Kernel(内核)镜像


![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480939466523.png)


**Step 4 . ** 将TF卡从电脑上拔下来，将TF卡插到pcduino板子上，给pcduino板子上电。

> 注意：
>  
> * pcduino板子只需要插上TF卡和接通电源即可，其他的什么设备都不需要连接。
> * 接通电源一定要是5V2A，最好是使用充电宝或者充电头直接给板子供电。**不可以使用电脑USB接口给板子供电。因为电流不够。**
> * 如果你真的使用电脑的USB接口给板子供电，后面板子安装系统镜像的时候，是不会成功的。

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480781160131.png)

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480779553594.png)

中间的LED4（TX）一1秒的间隔闪烁，说明正在烧写内核程序（pcduino板子全自动烧写），大约不到23秒钟左右，中间这个LED不在闪烁，说明：内核文件烧写完成。这时拔下TF卡，再将pcduino板子断开电源。


----------


## 给pcduino板子烧写Ubuntu NAND系统

**Step 1 . ** 再将TF卡通过读卡器连接到电脑，然后使用上面同样的方法（用**SD Formatter**软件）对TF卡进行格式化操作。


**Step 2 . ** 选择要烧写的镜像文件

将解压后的系统镜像文件（`pcduino3_ubuntu_20140807.img` 和 `update.sh`）直接拷贝到TF卡上。

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480782215024.png)

**Step 3 . ** 检查 `update.sh` 文件

如果你下载的这个：

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480940230049.png)

我们现在使用记事本软件打开`update.sh` 启动文件，检查里面指定的镜像文件名是否正确，可以看到，我现在这个情况，是不正确的：

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480780631220.png)

如果我们TF卡根目录里面的镜像文件名为：`pcduino3nano_ubuntu_20140807.img`。所以我们需要手动修改`update.sh` 文件：

将其修改为下面这样，并保存文件。

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480780787224.png)

总之，这一步（**Step 3 . **）的目的就是：让`update.sh`文件里面的`IMG`变量指向正确的镜像文件路径。

> **注意：** 如果你使用的镜像文件是：**pcduino3_ubuntu_20140807.img**，它是有GUI界面的；如果你使用的镜像文件是**pcduino3nano_ubuntu_20140807.img**，它是没有GUI界面的，它只有命令行界面。


**Step 4 . ** 给pcduino板子连接显示器，再接通电源：（这时pcduino板子还不插TF卡）

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480943598183.png)

这时观察pcduino连接的显示屏，当出现下面的信息时：

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480945409839.png)


**Step 5 . ** 现在将烧写好的系统的TF卡插到pcduino板子上。然后pcduino自动将TF卡里面的系统镜像安装到pcduino芯片里。（等待大约8分钟）


当你看看到下面的信息的时候，说明系统已经安装完成了。

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480944718209.png)


**Step 6 . ** 这个时候，关闭电源，你可以将SD卡去下来（TF卡已经没有用了，你可以把它扔了，呵呵）。

现在，给板子重新上电，板子自动运行系统。

![Alt text](/images/2016-12-5-pcduino-programming-sysytem-Ubuntu-NAND-image/1480945185981.png)

## 搞定

----------


参考网站：

* [Installing Ubuntu 14 on a pcDuino3B](https://www.youtube.com/watch?v=XXauYnwElpQ)
* [Pcduino烧写系统Pcduino 3 Nano 烧写系统小记](http://www.itdadao.com/articles/c15a578261p0.html)



