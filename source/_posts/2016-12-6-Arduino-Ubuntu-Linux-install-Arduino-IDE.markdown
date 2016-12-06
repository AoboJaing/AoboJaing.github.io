---
layout: post
title: "Arduino 002 — 在Ubuntu（Linux） 中搭建Arduino开发环境"
date: 2016-12-06 13:46:35 +0800
comments: true
sharing: true
categories: [Arduino]
tags: [Arduino, Ubuntu, Linux, IDE, 软件安装]
---

我的**Ubuntu**系统：**Ubuntu 14.04.10 TLS 32位**
需要安装的**Arduino**的版本：**Arduino 1.6.11（最新版本） Linux 32位**


## 1. 下载 最新的 **Arduino** 开发软件

**Step 1 . ** 到**Arduino**官网下载 **linux 32位** 的 **Arduino** 开发软件：
Web：https://www.arduino.cc/en/Main/Software

## 2. 解压

**Step 2 . ** 解压**arduino-1.6.11-linux32.tar.xz**
```
cd ~/Downloads
tar -xvJf arduino-1.6.11-linux32.tar.xz
```
![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-install-Arduino-IDE/1472642224393.png)

**Step 3 . ** 将解压后的文件（`arduino-1.6.11`）移动到 `/opt`  目录下：

```
cd ~/Downloads
sudo mv arduino-1.6.6 /opt
```

**Step 4 . ** 进入 `/opt/arduino-1.6.11` 文件夹，将**Files**窗口最大化。选中 **arduino** 文件，再在**菜单栏**中选择：**Edits** -> **Preferences**

![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-install-Arduino-IDE/1472642888060.png)

**Step 5 . ** 这时弹出下面的窗口。选择：**Behavior** 选项卡，将**Executable Text Files**项里面，勾选：**Ask each time** 单选框。

![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-install-Arduino-IDE/1472642984839.png)

## 3. 运行 **Arduino** 

现在你有两种方法运行 **Arduino** 软件：

**方法一：** 双击 **arduino** 文件： 弹出一个对话框，点击**Run**

![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-install-Arduino-IDE/1472555757325.png)

 
**方法二：**打开一个终端：路径切换到**arduino**文件所在路径（`/opt/arduino-1.6.11/`），运行它：

```
cd /opt/arduino-1.6.11/
./arduino
```

现在，恭喜你，已经安装成功了：

![Alt text](/images/2016-12-6-Arduino-Ubuntu-Linux-install-Arduino-IDE/1472555815898.png)


## 4. 做一些配置，实现在终端的任何路径下，都可以运行 **Arduino** 软件

使用`ln` 命令(给文件创建软链接文件) Web：http://roclinux.cn/?p=752

我们希望在终端的任何路径下，输入 `arduino` 都可以启动 **Arduino** 软件：

**Step 6 . ** 操作如下，打开一个终端，执行下面的命令。将 `/opt/arduino-1.6.6/arduino` 文件在 `/bin/` 路径下创建一个软链接文件。

```
sudo ln -s /opt/arduino-1.6.11/arduino /bin/
```

搞定，这样就可以在终端中，不管当前路径是什么，都可以启动**Arduino**了。

试试看。现在，在终端中直接执行：

```
arduino
```


## 5. 如何给 **Arduino** 板子，烧写程序

请见博客：Arduino 003 Ubuntu（Linux） 系统下，如何给板子烧写程序 。

## 搞定
