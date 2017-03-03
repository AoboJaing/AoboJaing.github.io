---
layout: post
title: "SolidWorks 如果装配体里面的的装配体有动态关节，如何让它活动"
date: 2017-02-22 03:47:59 +0800
comments: true
sharing: true
categories: [SolidWorks]
tags: [SolidWorks, 装配体]
---


----------

如果你在装配体里面插入一个装配体的话，如果被插入的装配体原本是有可动关节的，但是被插入后，可动的关节不能运动了。

要想让它还能动， 其他很简单，我们只需要这样做：

对着我们需要恢复可动的关节的转配体：

![Alt text](/images/2017-2-22-how-to-activation-Movable-joint-move-in-assembly/1487706079338.png)


然后将 **求解为** 选为 **柔性(F)**。（被插入到装配体中的装配体默认这一项是为 **刚性(R)**的。）

![Alt text](/images/2017-2-22-how-to-activation-Movable-joint-move-in-assembly/1487706131122.png)

现在转配体里面的包含的装配体的可动关节就可以动了。（如果可动的关节太多，你会明显的感觉到SolidWorks软件运行有点卡。）


----------




