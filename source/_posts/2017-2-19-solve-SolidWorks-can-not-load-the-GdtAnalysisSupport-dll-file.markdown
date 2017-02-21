---
layout: post
title: "解决 SolidWorks 无法装入 GdtAnalysisSupport.dll文件 的问题"
date: 2017-02-19 16:35:46 +0800
comments: true
sharing: true
categories: [SolidWorks]
tags: [SolidWorks, GdtAnalysisSupport.dll]
---


----------

昨天做好的零件文件，今天睡醒了，再次打开， 就出现了这个问题：`无法装入 SolidWorks.dll文件：GdtAnalysisSupport.dll`


![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487392359179.png)


----------

## 解决办法

参考网站：http://jingyan.baidu.com/article/72ee561a530355e16138dfd4.html


参考 

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487393791415.png)

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487393815563.png)

直接点击 **忽略** ：

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487393914660.png)

等待大约5分钟：

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487394450625.png)


![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487394522702.png)

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487394544788.png)


----------

现在启动 SolidWorks 软件：

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487394625073.png)

所以，你需要重新破解：

参考网站：

现在我们想点击 **我想以后激活我的SolidWorks产品**，来看看上面出现的问题是否解决了。

问题仍然存在：

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487394891003.png)

操了！


----------

我知道怎么回事了。在**注册表编辑器** 里面添加Installer的路径错了。

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487397304857.png)


![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487397342762.png)

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487397374349.png)


----------

----------

现在，`GdtAnalysisSupport.dll`文件的这个问题已经被解决了。现在SolidWorks软件是未被激活的状态，我们需要将其激活，激活的方法很简单，只需要到[这个](http://www.mfcad.com/solidworks/xiazai/18672.html)下载破解文件：

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487628031823.png)

然后将这个下载后的压缩包解压，然后将里面的`setup`文件夹整个复制到你安装SolidWorks软件的路径下， 我当前安装的路径是：`C:\Program Files\SolidWorks Corp\SolidWorks`。这个路径里面原本就是有一个`setup`文件夹。我们在复制的时候，电脑会提示我们，我们直接选择**替换**即可。现在无需重启电脑，直接启动SolidWorks软件，现在软件就不会在提示你**激活软件**了。

----------



## 出现一个问题

现在，这个问题是不在出现了，但是，我之前做好的模型，还是有一部分步骤都失效了。这是怎么回事。

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487405570583.png)

我现在没有办法了，现在的办法是：安装更新的SolidWorks 软件（2016）

请参考这篇笔记：**Windows 10 安装 SolidWorks 2016 Sp5.0**


----------

2017-2-18 16:12:01

其实可以不用安装 SolidWorks 2016软件，我知道为什么打开的模型会是上面这个样子的了：

那些 “**失效**” 的步骤其实是 被 **压缩** 了。

解决办法就是：我们只需要将这些“**失效**”的步骤给 **解除压缩**即可。

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487405886362.png)


----------

问题解决：

![Alt text](/images/2017-2-19-solve-SolidWorks-can-not-load-the-GdtAnalysisSupport-dll-file/1487405910127.png)
