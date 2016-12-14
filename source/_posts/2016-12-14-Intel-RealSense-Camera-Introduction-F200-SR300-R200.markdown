---
layout: post
title: "Intel RealSense 000 Intel RealSense摄像头介绍：F200、SR300、R200"
date: 2016-12-14 18:47:00 +0800
comments: true
sharing: true
categories: [Learning Intel RealSense SDK, Learning Intel RealSense librealsense]
tags: [Intel RealSense, F200, SR300, R200]
---

---


----------

目前的Intel RealSense摄像头一共有三款：**F200**、**SR300**、**R200**。

* SR300 和 F200 都属于：近距离摄像头（Front Facing）。
* R200 属于：远距离摄像头（Rear Facing）
* 在Intel RealSense 官方示例程序中，总会在程序的前缀出现：`FF_`、`RF_`或者`DF_`，它们分别表示：**适用于近距离摄像头**（Front Facing）、**适用于远距离摄像头**（Rear Facing） 和 **两者都适用**（Dual Facing）。


----------


## SR300

官网介绍：[Introducing the Intel® RealSense™ Camera SR300](https://software.intel.com/en-us/articles/introducing-the-intel-realsense-camera-sr300)

外部：

![Alt text](/images/2016-12-14-Intel-RealSense-Camera-Introduction-F200-SR300-R200/1481614405367.png)


内部：

![Alt text](/images/2016-12-14-Intel-RealSense-Camera-Introduction-F200-SR300-R200/1481614321225.png)

----------

![Alt text](/images/2016-12-14-Intel-RealSense-Camera-Introduction-F200-SR300-R200/1481614483853.png)

SR300 只有：

* 测量范围：0.2m ~ 1.2m （要求：室内，并且）
* 深度摄像头（640x480 60fps）
* 彩色摄像头（1080p 30fps 或者 720p 60fps 可调）
* 红外线摄像头（640x480 200fps ）
* 无**左**（left）、**右**（right）摄像头


----------

## R200


参考网站：[Developing for the Intel® RealSense™ Camera (R200)](https://software.intel.com/en-us/articles/realsense-r200-camera)

外部：

![Alt text](/images/2016-12-14-Intel-RealSense-Camera-Introduction-F200-SR300-R200/1481707509944.png)


内部：

![Alt text](/images/2016-12-14-Intel-RealSense-Camera-Introduction-F200-SR300-R200/1481707878472.png)

R200 有：

* 测量范围：

----------

## [Intel RealSense 测量范围](https://software.intel.com/en-us/articles/intel-realsense-data-ranges)

![Alt text](/images/2016-12-14-Intel-RealSense-Camera-Introduction-F200-SR300-R200/1481708072967.png)


