---
layout: post
title: "Intel RealSense 001 开发环境的选择"
date: 2016-12-14 18:58:23 +0800
comments: true
sharing: true
categories: [Learning Intel RealSense SDK, Learning Intel RealSense librealsense]
tags: [Intel RealSense, Intel RealSense SDK, librealsense]
---

---

> 不管你使用Intel RealSense的哪款摄像头，本文都适合你。

对于开发环境（就是你编写程序），你有两个选择：

* [Intel RealSense SDK](http://www.aobosir.com/blog/2016/12/07/Intel-RealSense-Windows-download-install-intel-RealSense-SDK/)（有要求：Windows 10系统）
* [librealsense](https://github.com/IntelRealSense/librealsense)（Intel RealSense跨平台API）


我个人推荐使用`librealsense`这个跨平台库，它让Intel RealSense摄像头在Linux系统上使用。并且同时可以在Linux系统里面的ROS机器人操作系统里面使用Intel RealSense。（[这里](http://wiki.ros.org/librealsense)）
