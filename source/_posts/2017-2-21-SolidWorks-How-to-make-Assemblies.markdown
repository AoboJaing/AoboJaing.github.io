---
layout: post
title: "SolidWorks 如何制作装配体"
date: 2017-02-21 17:25:20 +0800
comments: true
sharing: true
categories: [SolidWorks]
tags: [SolidWorks, 装配体]
---


----------

## 自底向上的装配体设计

我们以一个例子来学习如何制作装配体。

** 装配的概念.zip ** ： 链接：http://pan.baidu.com/s/1skBX41v 密码：kff7


这里有包含一个机器人的所有零件的压缩包，这里面都是单独的零件。

接下来，我们要做的事情就是将这些单独的零件制作成一个装配体。


----------

启动SolidWorks软件，然后先新建一个装配体：


![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487658790557.png)


![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487658814883.png)


点击 **浏览**：

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487658863593.png)


我们先选择其中的`RectBase.SLDPRT`零件。


![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487659234073.png)

直接点击 **确定**：

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487659308431.png)

这个时候，鼠标是和零件绑定在一起的，你鼠标移动到哪个位置，零件就到哪个位置。当你鼠标一点击，那么零件就会固定在这个位置上了。这是不行的。（这个时候是关键了）如果你鼠标随便的一点击，零件固定在一个位置，你不知道它被放在了什么位置。你根本就不知道。

正确的做法：

装配体里面有一个默认的原点，就是`(0, 0)`点，同时零件本身也有一个零点。我们现在需要做的事情是：将这个零件的原点与这个装配体的原点重合。如何重合，很简单：可视化窗口里面不需要点击鼠标，将鼠标移动到设计树这边，我只需要点击 上面对号（就是 **确定**的意思）。软件会自动帮我们将第一个零件固定。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487660511203.png)


----------

这样，我们就成功的在装配体中插入了第一个零件。（插入第一个零件的要点就是：必须要将零件的原点与装配件的原点重合。）


----------


接着，我们插入第二个零件。还是一样：

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487664083112.png)


点击 **浏览**：

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487664127950.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487664146709.png)

对于第二个和第三个零件，我们就可以随便点了。我们只需要在这个可视化界面里面随便点一下。

和插入第二个零件一样的方法，将第三个零件插入到装配件里面。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487664299248.png)


----------

好的，零件都放进来了，现在我们就要开始装配了。

## 随便说一下，在装配体中，鼠标的作用

当鼠标选中了一个零件，按住鼠标左键，就是移动这个零件。鼠标的滚轮还是缩放的功能。鼠标中间按住不松口，就是整个视角上的旋转（看不同方式上的视图）。鼠标右键还是一样是选择菜单。如果是使用鼠标右键选中这个零件后，然后鼠标右键按住不动，那么就是真正的对单个零件的旋转。

这就是装配体中，对鼠标的基本操作。现在熟悉了鼠标，现在我们就来开始做装配。


----------

一个零件在空间中有六个自由度，其中三个是平移，三个是旋转。我们要做的事情就是限制这些自由度，自由度限定死了，那么它就在空间中完全固定下来了，就不会随便乱动了。

如果你留一个自由度在那，那么它就是一个会旋转的装配体。所以，简单的说：做装配体就是限制零件在空间中的自由度。（所以做装配体是很简单的。）


----------

现在，我们就来限制这些零件的自由度。

限制零件的自由度，其实就是做**配合**。

我们现在就做第一个导入的零件和第三个导入的零件进行**配合**。

先点击 **配合** 工具 ：


![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487664893082.png)

分部选择两个零件的需要重合的面。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487666994345.png)

配合好了，就可以点击**确定**了。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487667075053.png)

配合一般都是进行连续配合。所以，你配合了一次，是不会退出配合命令的，我们还会继续进行接下来的几次配合。

接下来就是使用同样的方法，进行配合了。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487667253911.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487667371108.png)

这样，我们就将第一个零件和第二个零件完全的配合了，它们现在已经被完全的定义了。现在点击 **确定** 图标来退出**配合**操作。


----------


现在使用同样的道理，现在来装配第二个零部件。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487667808835.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487667837627.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487667899899.png)


----------

现在，三个零件都装配好了。现在我们就可以点击 **确定** 按钮来退出**配合**操作。


----------



在装配体里面，千万不要选择镜像。镜像会出现一个什么样的效果：镜像会产生一个新的零部件。这跟我们在零部件的状态下生成镜像是一样的。

那么我现在要做装配件的另外一面，我要怎么做：就是复制这个零件。

## 如何复制零件

按住 **Ctrl **键，然后鼠标左键不要松开，推动这跟零件，这样就复制出来了。复制完之后，松开 **Ctrl** 键完成复制。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668280693.png)

然后，我们在使用上面同样的操作，再对复制出来的零部件进行同样操作，将其装配到装配体上。

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668500372.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668586382.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668698857.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668724875.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668773121.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668802776.png)

![Alt text](/images/2017-2-21-SolidWorks-How-to-make-Assemblies/1487668840052.png)


----------


## 搞定
