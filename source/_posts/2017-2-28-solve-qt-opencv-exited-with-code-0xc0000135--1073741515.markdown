---
layout: post
title: "解决问题：Qt5 OpenCV “uring startup program exited with code 0xc0000135”  “ exited with code -1073741515”"
date: 2017-02-28 14:29:00 +0800
comments: true
sharing: true
categories: [Qt, OpenCV]
tags: [exited with code 0xc0000135, exited with code -1073741515, Windows, Qt5, OpenCV, 环境变量]
---


----------

## 前言

之前已经搭建好的Qt5 和 OpenCV的环境（并且我之前写过博文，在[这里](http://blog.csdn.net/github_35160620/article/details/52364252)），今天我运行了一下之前可以运行的程序， 竟然出现了问题：

代码：

```cpp
#include <QCoreApplication>
#include <opencv2/highgui/highgui.hpp>
#include <opencv2/imgproc/imgproc.hpp>
#include <opencv2/core/core.hpp>

int main(int argc, char *argv[])
{
    QCoreApplication a(argc, argv);

    cv::Mat image = cv::imread("..\\helloWorld\\image.jpg");
    cv::namedWindow("Image");
    cv::imshow("Image", image);

    cv::waitKey(0);
    return a.exec();
}

```

配置：

```cpp
QT += core
QT -= gui

CONFIG += c++11

TARGET = helloWorld
CONFIG += console
CONFIG -= app_bundle

TEMPLATE = app

SOURCES += main.cpp

INCLUDEPATH+=C:\third_packages\opencv\opencv2410-qt5\include\opencv \
             C:\third_packages\opencv\opencv2410-qt5\include\opencv2 \
             C:\third_packages\opencv\opencv2410-qt5\include

LIBS+=  C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_calib3d2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_contrib2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_core2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_features2d2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_flann2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_gpu2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_highgui2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_imgproc2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_legacy2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_ml2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_nonfree2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_objdetect2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_ocl2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_photo2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_stitching2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_ts2410.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_video2410.dll.a \
        C:\third_packages\opencv\opencv2410-qt5\lib\libopencv_videostab2410.dll.a \

```

----------

##  出现的问题

调试的时候出现了下面的错误：

![Alt text](/images/2017-2-28-solve-qt-opencv-exited-with-code-0xc0000135--1073741515/1488257248592.png)

![Alt text](/images/2017-2-28-solve-qt-opencv-exited-with-code-0xc0000135--1073741515/1488257255314.png)

![Alt text](/images/2017-2-28-solve-qt-opencv-exited-with-code-0xc0000135--1073741515/1488257261932.png)

运行程序的时候，什么的没有。但是在**应用程序输出栏里面有这面截图是如数**

![Alt text](/images/2017-2-28-solve-qt-opencv-exited-with-code-0xc0000135--1073741515/1488257401005.png)

![Alt text](/images/2017-2-28-solve-qt-opencv-exited-with-code-0xc0000135--1073741515/1488257952750.png)


我简单的用语言叙述一下出现的这个问题：

当我点击运行的时候，程序会弹出黑色的终端窗口，在**应用程序窗口**里面，程序会显示自动退出，然后代码是：**-1073741515**。

我想研究一下，究竟是什么地方出现看错误，所以，我点击 **调试** 按钮，然后就出现了上面三个错误提示窗口。

----------


## 解决办法

在我没有上网上找解决办法之前，我猜测是因为我后来在电脑上安装了什么软件或者又搭建了什么环境，然后可能是影响到了Qt 和 OpenCV 的开发环境了，可能是被神不知鬼不觉的给改了什么地方。

网上说：是因为环境变量没有添加的原因，但是我之前都添加过环境变量了。我想可能是因为其他的软件把我添加的环境变量个删除了或者挤下去了。所以现在我来查看一下当前的环境变量：

通过查看，环境变量都在：


----------

我使用下面的程序测试Qt5软件。程序是可以正常运行的。正常的输出的 `Hello World!`。

```cpp
#include <QCoreApplication>
#include <opencv2/highgui/highgui.hpp>
#include <opencv2/imgproc/imgproc.hpp>
#include <opencv2/core/core.hpp>

#include <iostream>

int main(int argc, char *argv[])
{
    QCoreApplication a(argc, argv);

//    cv::Mat image = cv::imread("..\\helloWorld\\image.jpg");
//    cv::namedWindow("Image");
//    cv::imshow("Image", image);

//    cv::waitKey(0);
    std::cout << "Hello World!" << std::endl;
    return a.exec();
}
```


----------

我刚刚再次查看了一下系统的环境变量，还真的发现：OpenCV-Qt的编译生成的`bin`的路径不在了。（也不知道是我之前根本就没有添加，我也忘记了）

将我之前编译的OpenCV-Qt的`bin`路径添加到当前的系统的环境变量里面：

![Alt text](/images/2017-2-28-solve-qt-opencv-exited-with-code-0xc0000135--1073741515/1488262534186.png)


然后现在，关掉Qt软件（必须要关闭，然后重新启动）。然后重新启动Qt5软件。

现在再次运行程序，问题解决：

![Alt text](/images/2017-2-28-solve-qt-opencv-exited-with-code-0xc0000135--1073741515/1488262593875.png)


