---
layout: post
title: "Arduino 003 Ubuntu（Linux） 系统下，如何给板子烧写程序"
date: 2016-12-06 13:51:56 +0800
comments: true
sharing: true
categories: [Arduino]
tags: [Arduino, Ubuntu, Linux, IDE]
---

使用的虚拟机软件：**VMware 11**
我的**Ubuntu**系统：**Ubuntu 14.04.10 TLS**
**Arduino** 软件的版本：**Arduino 1.6.11**
**Arduino** 板子的型号：**Arduino UNO R3**

**Step 0 . ** 来到 **VMware** 虚拟机里的**Ubuntu **系统的界面。

**Step 1 . ** 将 **Arduino** 板子通过USB线插到电脑上。

**Step 2 . ** 在终端中执行下面的命令，来启动 **Arduino** 软件。
```
arduino
```

**Step 3 . ** 随便打开一个程序。我们以 **Blink** 程序为例，打开它：
![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472659956768.png)

**Step 4 . ** 选择 **板卡型号**
![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660070620.png)

**Step 5 . ** 选择当前 **端口号**
![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660146798.png)

> 你可以看到：**Arduino** 软件右下角有当前被选中的端口号和被选中的**Arduino**板卡的信息。
> 
>![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660193423.png)

**Step 6 . ** 给端口添加权限。

> 如果，这时你给 **Arduino** 开发板下载程序，发现下载出错。原因就是没有给端口添加权限。
> 
> ![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660225037.png)
> 输出的 **error** 提示：
>```
avrdude: ser_open(): can't open device "/dev/ttyACM0": Permission denied
>```

在终端中执行下面的命令，来给当前选中的端口添加权限。
```
sudo chmod a+rw /dev/ttyACM0
```

> 端口号都在`/dev/` 目录里面。执行下面的命令可以查看：
> ```
> cd /dev/
> ls
> ```
> 输出 如下图所示：
> ![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660593893.png)

---

> **注意：** 如果你将**Arduino** 板子插到电脑上了，但是在**/dev/** 目录里面没有在到类似 `ttyACM0` 这样的端口号。
> 解决办法，将**Arduino**板子从电脑的USB口拔出，将当前屏幕界面切换到**VMware** 虚拟机里的**Ubuntu **系统的界面，这时，再将**Arduino** 板子插到电脑上。你就可以在`/dev/`路径里面找到类似 `ttyACM0` 这样的端口号了。


**Step 6 . ** 点击 **编译** 按钮
![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660394610.png)


**Step 7 . ** 点击 **上传** 按钮
![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660434092.png)

> 其实，可以不用点击 **编译** 按钮，直接点击 **上传** 按钮就可以。因为点击完 **上传** 按钮后，它会再编译一遍，在将程序烧写到板子上。

现在提示 **Done uploading**，表示程序已经成功烧写到板子里面。
![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-board-upload-program/1472660284963.png)

## 搞定


