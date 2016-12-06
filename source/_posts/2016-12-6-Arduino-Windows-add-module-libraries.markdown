---
layout: post
title: "Arduino 004 Windows上给Arduino IDE添加模块库"
date: 2016-12-06 13:54:54 +0800
comments: true
sharing: true
categories: [Arduino]
tags: [Arduino, IDE, libraries, module]
---

----------


在我的Windows电脑里面，Arduino IDE软件安装在`C:\Program Files (x86)\Arduino`路径里面。

我们以一个例子来说明，如果将模块库添加到Arduino IDE软件中。

## 添加 I2Cdev 及其相关模块库到Arduino IDE软件里面

**Step 0 . ** 关闭 Arduino IDE 软件

**Step 1 . ** 下载 i2cdev 及其相关的模块库

到[这个网址](https://github.com/jrowberg/i2cdevlib)里面下载所有i2cdev相关的模块库。

**Step 2 . ** 下载后，解压，将`/Arduino/`路径里面的所有文件夹复制，并拷贝到：`C:\Program Files (x86)\Arduino\libraries`路径里面。

![Alt text](/images/2016-12-6-Arduino-Windows-add-module-libraries/1481001787595.png)

**Step 3 . ** 启动Arduino IDE 软件。在 **文件** -> **示例** 里面就可以看到刚刚添加到Arduino IDE的模块库。（现在就可以正常使用了）

![Alt text](/images/2016-12-6-Arduino-Windows-add-module-libraries/1481001851166.png)


----------

> 注意：
>  
> 如果是Ubuntu系统，Arduino IDE 一般被安装在：`/opt/arduino/`

