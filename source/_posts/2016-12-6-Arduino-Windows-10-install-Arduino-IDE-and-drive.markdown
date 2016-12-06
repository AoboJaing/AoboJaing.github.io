---
layout: post
title: "Arduino 001 Windows 10 安装Arduino IDE软件 和 驱动"
date: 2016-12-06 13:37:20 +0800
comments: true
sharing: true
categories: [Arduino]
tags: [Arduino, Windows, IDE, 软件安装, 驱动]
---


----------

> 在Win10 上安装最新的Arduino IDE （1.6.9安装包）很简单，并且不行要手动安装Arduino板子的驱动，整个安装过程都当前的简单，我以前在我的Win7系统上安装Arduino1.1.0时，需要手动安装板卡驱动，步骤相当繁琐。

## 1. 先连接**Arduino**与电脑。

## 2. 下载Arduino IDE软件

然后，到[这个网址](https://www.arduino.cc/en/Main/Software) （这个网站打开时，有点慢。）下载最新的Arduino IDE 软件。（记住安装路径，因为后面要用上。）
![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469421628198.png)

## 3. 安装驱动

打开**控制面板** -> 设备管理器 -> 端口

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469421740222.png)

驱动已经安装成功。

## 4. 测试Arduino IDE软件是否可以使用：

### 选择办卡：Arduino/Genuino Uno

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469421799260.png)

### 然后，选择端口：

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469421867289.png)

### 测试：随便导入一个程序：`Blink`

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469421937550.png)

### 点击：**验证**

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469421954757.png)

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469422001208.png)

### 点击：**上传**

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469422032515.png)

![Alt text](/images/2016-12-6-Arduino-Windows-10-install-Arduino-IDE-and-drive/1469422051312.png)

## 实验现象

现在看到的实验现象就是：板子上的A13的LED在闪烁。

# 搞定



---

参考网站：

https://www.arduino.cc/en/Guide/Windows?setlang=cn

其他网站，没有用上：

http://www.arduino.cn/thread-1008-1-1.html
