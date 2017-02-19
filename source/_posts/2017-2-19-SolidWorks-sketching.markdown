---
layout: post
title: "Solidworks 草图绘制"
date: 2017-02-19 16:03:44 +0800
comments: true
sharing: true
categories: [SolidWorks]
tags: [SolidWorks, 草图绘制]
---


----------

## 如何新建一个文件

![Alt text](/images/2017-2-19-SolidWorks-sketching/1485927554653.png)


----------

鼠标点击 **前视基准面**，然后鼠标不要动，会在鼠标右上角出现一条图标：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1485928241107.png)

第一个是：**绘制草图**

![Alt text](/images/2017-2-19-SolidWorks-sketching/1485928516663.png)


----------

第二个是：**正视于**

![Alt text](/images/2017-2-19-SolidWorks-sketching/1485928543023.png)


----------

当你点击**绘制草图** 这个图标。视图中会自动的将**前视基准面** 正对着你。（当然这是你第一个这样操作的时候，会这样。如果视图中已经有模型存在了，那么它就不会这样做了。）

同时还会在左侧的列表里面增加了一个![Alt text](/images/2017-2-19-SolidWorks-sketching/1485928807493.png)


![Alt text](/images/2017-2-19-SolidWorks-sketching/1485928772388.png)

所以，对于第一次点击 **草图绘制**，它是做了两步操作：选择一个基准面，然后**正视于**你。


----------

你在视图右下角可以看到：**正在编辑：草图1**

![Alt text](/images/2017-2-19-SolidWorks-sketching/1485929231348.png)


----------

现在就是正在编辑草图的状态，我们可以开始画草图了。


----------

画草图的第一个原则：就是**草图必须跟原点发生关系**。（如果一个物体在空间中跟原点没有关系，这个物体的位置在空间中就定义不了。它是浮动的，它跟原点没有任何关系。）所以，需要跟原点产生关系。

关系一般就是：几何约束 或者 尺寸约束。（根据你自己的模型的特点来定。）


----------

选择**直线**命令：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1485931152305.png)

然后鼠标移动到原点上面，当鼠标移动到原点上面的时候，会出现下面这个图标：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486022516663.png)

出现上面的图标，说明，原点与当前鼠标点的几何关系是重合。这个时候鼠标点下去。然后就可以松开。（一个点画完之后，就可以马上松开。）

松开之后，我们在画一条竖直的 直线。注意鼠标的反馈信息。你会看到现在出现一个图标，当你看到现在这个图标，说明当前的直线是竖直的。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486022844406.png)

在点击一下鼠标左键，一条直线就画好了。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486022892530.png)


----------

接下来，我们绘制一段圆弧：先将鼠标放置在一点，此时会出现下面的图标：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486022995558.png)

然后将鼠标移上去。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023020758.png)

然后在想右移，圆弧就出来了：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023059691.png)

快捷键：直线变成圆弧，圆弧变成直线： **A**


----------

此时，你会看到一个十字交叉的线，这个线叫做：推理线。

如果我们绘制的线（虚线）在下面这个位置，那么它的几何关系就是：进过圆弧的中心。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023372171.png)

如果是下面这个情况，鼠标的反馈信息是：相切。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023360816.png)

鼠标点下去，会这条直线。

然后在将鼠标移动到下面这个位置：（出现两个几何关系：一个水平，一个竖直）

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023457105.png)

画下去，最后闭合：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023607424.png)


----------

接下来，我们的目标是画槽：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023684882.png)


命令在这里：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486023792344.png)

当我们选择这个命令后，我们会看到，左侧出现的**槽口**窗口，我们选择的就是第一个命令。你可以看到这个图标里面有`1`、`2`、`3`。它们代表的意思顾名思义：就是鼠标第一下点的是这个圆弧的中心，第2下点的是第二个圆弧的中心，第3下点鼠标是圆弧的半径，就是宽度。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486024090462.png)


然后，我们将 **添加尺寸** 复选框选中。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486024798934.png)


----------

如何做到：让一个绘制出的直线平行与已知直线。

第一步靠近要平行的直线，然后停一停，推理线就出来了：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486024567374.png)

第二步：移动到推理线上。


![Alt text](/images/2017-2-19-SolidWorks-sketching/1486024615305.png)

这样，一个槽就画好了。它就自动的添加了两个尺寸。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486024847643.png)


----------

扩展：如果两个分来的直线，然后我们让他它们两个的几何关系是平行的，我们如何手动添加呢？

我们先选中一条直线，然后按住**Ctrl**键选中另一条。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486025169184.png)

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486025226649.png)

----------


现在轮廓已经画好了。现在我们就来标注尺寸。大多数的尺寸，我们都可以使用 **智能尺寸** 命令来标注。

快捷键：**S**，弹出一个工具栏，第二个图标就是**智能尺寸**

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486025375647.png)
 
点一下需要标注的直线。然后鼠标放到合适的位置，然后在点击一下鼠标。然后输入尺寸，即可，很简单。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486025553704.png)

圆弧半径的标注也是一样的简单，点一下圆弧就可以了。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486025541470.png)


----------

两条直线之间的距离如何标注：

点一下一个直线，然后在点击另一个直线，然后将尺寸放置在合适的位置，点一下鼠标，然后就可以标注尺寸了。


----------

在标注尺寸的时候，你有没有发现一个现象：当我们没有标注尺寸之前，草图的线是蓝色的（就是：欠定义状态），但是当我们标注了尺寸之后，线就变成了黑色。黑色代表的是：完全定义。

如果当你标注的尺寸出现了逻辑上的错误，那么直线就会以红色显示。 


----------

现在就完全定义了。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486026142063.png)


----------

圆与圆之间 最近距离的智能尺寸如何添加：

点击其中一个圆的比较靠近的边，然后按住**Shift**，然后在点击另一个圆比较靠近的边。

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486026391771.png)


----------

同样的道理，可以添加最远的智能尺寸 和 一个圆最远和一个圆最近的智能尺寸：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486026441757.png)

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486026492761.png)


----------

当我们编辑完草图后，我们点击右上角的 **完成编辑** 按钮：（注意不要点击那个叉，如果你点击了那个叉，那么你绘制的草图就没有了，消失了。）

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486026703297.png)


----------

现在自动跳到了实体菜单里面：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486026797681.png)


----------



![Alt text](/images/2017-2-19-SolidWorks-sketching/1486026932475.png)

当你点击了 **拉伸凸台/基体** 你会看到，现在草图变成了灰色的。因为拉伸是基于草图的，你需要选择一个草图，拉伸的是草图。

我们现在草图已经画好了，只需要选择一个草图就可以了。只需要鼠标左键点一个草图的一个边，然后点击**确定**：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486027138904.png)


----------

那么做一个零件模型的整个流程就做完了。


----------

接下来，介绍如何画：草图的圆角。

先随便绘制一组线：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486027981617.png)


----------

然后快捷键 **S**，选择里面的 **圆角** 命令：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028007306.png)

鼠标放在 一个点上，就会出现圆角：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028167894.png)

鼠标点中即可。然后我们给每一个点添加圆角：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028234848.png)

你可以在左侧设置圆角参数：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028251098.png)

设置完成后，我们点击 确定图标，即可：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028282061.png)


----------

你看可以看到，如果我们想要给断的两端的线添加一个圆角，我们要怎么做呢。

很简单，选中一端的线，然后在将鼠标放到另一端，圆角就出现了：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028507916.png)

确定即可：

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028534798.png)


----------

![Alt text](/images/2017-2-19-SolidWorks-sketching/1486028600613.png)
