---
layout: post
title: "解决OpenNI问题：XnOS.h：No such file or directory"
date: 2017-02-11 07:51:03 +0800
comments: true
sharing: true
categories: [OpenNI]
tags: [No such file or directory, OpenNI]
---

----------

参考网站：[ofxOpenNI：XnOpenNI.h：没有这样的文件或目录](https://forum.openframeworks.cc/t/ofxopenni-xnopenni-h-no-such-file-or-directory/14286)


----------

## 遇到的问题

```
XnOS.h: No such file or directory
```

![Alt text](/images/2017-2-11-solve-openni-XnOS-No-such-file-or-directory/1486745884346.png)


----------

## 解决办法

查找`openni`相关的软件包。

```
aobo@aobo-tp:~$ apt-cache search openni
libopenni-dev - headers for OpenNI 'Natural Interaction' frameworks
libopenni-java - Java framework for sensor-based 'Natural Interaction'
libopenni-sensor-pointclouds-dev - headers for Kinect sensor modules for the OpenNI framework
libopenni-sensor-pointclouds0 - Microsoft Kinect sensor modules for the OpenNI framework
libopenni-sensor-primesense-dev - headers for working with PrimeSense sensor OpenNI modules
libopenni-sensor-primesense0 - PrimeSense sensor modules for the OpenNI framework
libopenni0 - framework for sensor-based 'Natural Interaction'
libopenni2-0 - framework for sensor-based 'Natural Interaction'
libopenni2-dev - headers for OpenNI 'Natural Interaction' frameworks
openni-doc - developer documentation for OpenNI frameworks
openni-utils - debug and test utilities OpenNI framework
openni2-doc - developer documentation for OpenNI frameworks
openni2-utils - debug and test utilities OpenNI2 framework
primesense-nite-nonfree - OpenNI module providing gesture and skeleton tracking
ros-kinetic-depth-image-proc - Contains nodelets for processing depth images such as those produced by OpenNI camera.
ros-kinetic-ecto-openni - Ecto bindings for the openni sensor.
ros-kinetic-freenect-camera - A libfreenect-based ROS driver for the Microsoft Kinect.
ros-kinetic-freenect-launch - Launch files for freenect_camera to produce rectified, registered or disparity images.
ros-kinetic-openni-camera - A ROS driver for OpenNI depth (+ RGB) cameras.
ros-kinetic-openni-launch - Launch files to open an OpenNI device and load all nodelets to convert raw depth/RGB/IR streams to depth images, disparity images, and (registered) point clouds.
ros-kinetic-openni2-camera - Drivers for the Asus Xtion and Primesense Devices.
ros-kinetic-openni2-launch - Launch files to start the openni2_camera drivers using rgbd_launch.
```

安装 `libopenni-dev` ：

```
aobo@aobo-tp:~$ sudo apt-get install libopenni-dev 
[sudo] password for aobo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libopenni-dev is already the newest version (1.5.4.0-14).
libopenni-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-57-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-57-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 140 not upgraded.
aobo@aobo-tp:~$ 
```

检测安装路径：

```
aobo@aobo-tp:~$ dpkg -L libopenni-dev
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libopenni-dev
/usr/share/doc/libopenni-dev/copyright
/usr/include
/usr/include/ni
/usr/include/ni/XnEnumerationErrors.h
/usr/include/ni/Linux-Powerpc
/usr/include/ni/Linux-Powerpc/XnPlatformLinux-Powerpc.h
/usr/include/ni/XnProfiling.h
/usr/include/ni/XnCppWrapper.h
/usr/include/ni/XnStack.h
/usr/include/ni/XnModuleInterface.h
/usr/include/ni/XnDump.h
/usr/include/ni/XnGeneralBuffer.h
/usr/include/ni/XnInternalDefs.h
/usr/include/ni/XnOpenNI.h
/usr/include/ni/XnStringsHashT.h
/usr/include/ni/XnOS.h
/usr/include/ni/XnMacros.h
/usr/include/ni/XnModuleCppInterface.h
/usr/include/ni/XnBaseNode.h
/usr/include/ni/XnDataTypes.h
/usr/include/ni/XnFPSCalculator.h
/usr/include/ni/XnCodecIDs.h
/usr/include/ni/XnPropNames.h
/usr/include/ni/XnUtils.h
/usr/include/ni/XnOSStrings.h
/usr/include/ni/XnUSB.h
/usr/include/ni/XnCyclicQueueT.h
/usr/include/ni/XnLicensing.h
/usr/include/ni/XnQueue.h
/usr/include/ni/XnArray.h
/usr/include/ni/XnStackT.h
/usr/include/ni/XnModuleCppRegistratration.h
/usr/include/ni/XnCallback.h
/usr/include/ni/XnDerivedCast.h
/usr/include/ni/XnDumpWriters.h
/usr/include/ni/XnHash.h
/usr/include/ni/XnOSMemory.h
/usr/include/ni/XnModuleCFunctions.h
/usr/include/ni/XnStatusCodes.h
/usr/include/ni/XnPrdNodeInfoList.h
/usr/include/ni/Linux-Mips
/usr/include/ni/Linux-Mips/XnPlatformLinux-Mips.h
/usr/include/ni/XnStringsHash.h
/usr/include/ni/XnLog.h
/usr/include/ni/XnBitSet.h
/usr/include/ni/XnTypes.h
/usr/include/ni/XnThreadSafeQueue.h
/usr/include/ni/XnStatusRegister.h
/usr/include/ni/XnVersion.h
/usr/include/ni/XnAlgorithms.h
/usr/include/ni/XnPlatform.h
/usr/include/ni/XnEventT.h
/usr/include/ni/Linux-AArch64
/usr/include/ni/Linux-AArch64/XnPlatformLinux-AArch64.h
/usr/include/ni/Linux-x86
/usr/include/ni/Linux-x86/XnOSLinux-x86.h
/usr/include/ni/Linux-x86/XnPlatformLinux-x86.h
/usr/include/ni/XnPrdNode.h
/usr/include/ni/MacOSX
/usr/include/ni/MacOSX/XnPlatformMacOSX.h
/usr/include/ni/XnEvent.h
/usr/include/ni/IXnNodeAllocator.h
/usr/include/ni/XnListT.h
/usr/include/ni/XnContext.h
/usr/include/ni/XnPrdNodeInfo.h
/usr/include/ni/XnOSCpp.h
/usr/include/ni/XnCyclicStackT.h
/usr/include/ni/XnQueueT.h
/usr/include/ni/XnList.h
/usr/include/ni/XnStatus.h
/usr/include/ni/XnNodeAllocator.h
/usr/include/ni/XnLogTypes.h
/usr/include/ni/Linux-Arm
/usr/include/ni/Linux-Arm/XnPlatformLinux-Arm.h
/usr/include/ni/XnQueries.h
/usr/include/ni/XnLogWriterBase.h
/usr/include/ni/XnNode.h
/usr/include/ni/XnScheduler.h
/usr/include/ni/XnUSBDevice.h
/usr/include/ni/XnHashT.h
/usr/lib
/usr/lib/pkgconfig
/usr/lib/pkgconfig/libopenni.pc
/usr/share/doc/libopenni-dev/changelog.Debian.gz
/usr/lib/libnimCodecs.so
/usr/lib/libSample-NiSampleModule.so
/usr/lib/libnimRecorder.so
/usr/lib/libnimMockNodes.so
/usr/lib/libOpenNI.so
/usr/lib/libOpenNI.jni.so
aobo@aobo-tp:~$ 

```

看一下`include`路径里面的`openni`文件：

```
aobo@aobo-tp:~$ cd /usr/include/ni/
aobo@aobo-tp:/usr/include/ni$ ls
IXnNodeAllocator.h  XnCodecIDs.h           XnFPSCalculator.h  XnModuleCFunctions.h          XnPrdNode.h          XnStatus.h
Linux-AArch64       XnContext.h            XnGeneralBuffer.h  XnModuleCppInterface.h        XnPrdNodeInfo.h      XnStatusRegister.h
Linux-Arm           XnCppWrapper.h         XnHash.h           XnModuleCppRegistratration.h  XnPrdNodeInfoList.h  XnStringsHash.h
Linux-Mips          XnCyclicQueueT.h       XnHashT.h          XnModuleInterface.h           XnProfiling.h        XnStringsHashT.h
Linux-Powerpc       XnCyclicStackT.h       XnInternalDefs.h   XnNodeAllocator.h             XnPropNames.h        XnThreadSafeQueue.h
Linux-x86           XnDataTypes.h          XnLicensing.h      XnNode.h                      XnQueries.h          XnTypes.h
MacOSX              XnDerivedCast.h        XnList.h           XnOpenNI.h                    XnQueue.h            XnUSBDevice.h
XnAlgorithms.h      XnDump.h               XnListT.h          XnOSCpp.h                     XnQueueT.h           XnUSB.h
XnArray.h           XnDumpWriters.h        XnLog.h            XnOS.h                        XnScheduler.h        XnUtils.h
XnBaseNode.h        XnEnumerationErrors.h  XnLogTypes.h       XnOSMemory.h                  XnStack.h            XnVersion.h
XnBitSet.h          XnEvent.h              XnLogWriterBase.h  XnOSStrings.h                 XnStackT.h
XnCallback.h        XnEventT.h             XnMacros.h         XnPlatform.h                  XnStatusCodes.h
aobo@aobo-tp:/usr/include/ni$ 

```

我们现在查看一下`openni`安装的头文件和链接文件：

下面这两个命令是检测不到`openni`的头文件路径的。
```
aobo@aobo-tp:/usr/include/ni$ pkg-config --cflags openni
Package openni was not found in the pkg-config search path.
Perhaps you should add the directory containing `openni.pc'
to the PKG_CONFIG_PATH environment variable
No package 'openni' found
aobo@aobo-tp:/usr/include/ni$ pkg-config --cflags ni
Package ni was not found in the pkg-config search path.
Perhaps you should add the directory containing `ni.pc'
to the PKG_CONFIG_PATH environment variable
No package 'ni' found
aobo@aobo-tp:/usr/include/ni$ 
```

正确的命令：

```
aobo@aobo-tp:~$ pkg-config --cflags libopenni
-I/usr/include/ni
aobo@aobo-tp:~$ pkg-config --libs libopenni
-lOpenNI
aobo@aobo-tp:~$ 
```


----------


我当前的项目是在QT中的，解决办法就是：

在 `.pro` 文件里面，添加`openni`的头文件路径和链接文件路径。

```
INCLUDEPATH += /usr/include/ni

LIBS += -L/usr/lib -lOpenNI
```
