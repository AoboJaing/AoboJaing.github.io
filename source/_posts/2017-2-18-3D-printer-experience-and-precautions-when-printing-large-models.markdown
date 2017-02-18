---
layout: post
title: "3D 打印大型模型时的经验和注意事项"
date: 2017-02-18 22:09:58 +0800
comments: true
sharing: true
categories: [3D打印]
tags: [3D打印, 大型模型, 注意事项, 经验]
---


----------

1 . 注意 需要注意电源线一定要插好，插牢，不可以断电了。

> 我之前一次，就是，电源线插头由于没有插紧，打到一半的，断电了。

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485307588623.png)


----------

2 . 同时挤出料的步进电机的位置的PLA料线要下面这个样子摆放：

简单的说：就是，靠近挤出料步进电机的PLA线，它不可以在顶部框里面太多圈，最好、最理想的是一圈，就像下图这样：

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485308021035.png)

> 错误的放法：（这是非常不可以的做法，因为这样会导致，在挤出PLA线的步进电机连接PLA线圈的那端的入口，入口出在运行一会儿的时间后，会出现死扣现象。）
>  
> ![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485309295046.png)



3 . 同时要注意：要不断的转动：（逆时针转动）

> 这样做的好处是：防止打印一段时间后，PLA线出现拧紧现象。

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485307763855.png)


----------

3 . 最好要使用SD卡，就是将生成的程序保存到SD卡里面，然后在使用读取SD卡的方式来进行打印。（详细的通过SD卡打印模型的介绍，请参考这篇笔记：使用SD卡打印模型）

> 使用SD卡的好处是：
>  
> 主要是这个软件的原因，如果我们不将生成的程序保存到SD卡上而是直接使用实时的方式，让电脑控制打印机，这个软件消耗的内存特别大：4700M多的内存，我的天啊，每次都是打印到不一会儿，就提示内存不足，然后软件自动异常关闭，然后打印就停止了。
>  
> 而使用SD卡就可以解决这个问题：
>  
> 你可以看到，现在所消耗的内存就很小了。属于正常的情况了。
>  
> ![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485304742210.png)

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485303479812.png)

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485303763458.png)


----------

在SD卡启动打印，和在电脑启动打印，在开始的时候是一样的：先加入热床，然后出料口移动到热床位置，然后加入挤出口。热床的温度和挤出口的温度都达到了指定的温度后，就开始打印了。

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485304615579.png)

> 但是使用SD卡时，比较奇怪的是：当先加热热床的时候，两个（热床和挤出口）都显示的是：关闭 状态。热床的当前温度在不断的上升，当热床达到指定温度后（显示方面，是不能判断热床是否加入热成功的。），热床还是显示为：关闭状态，它的`/`右侧仍然没有变成指定的指定温度。接着挤出头下降，挤出头开始升温。升到指定温度。打印机就开始工作了。
> 
> ![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485304630660.png)


----------

得到的模型：

正面：

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485310579275.png)


反面：

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485310602262.png)


----------

用砂纸处理后：

正面：

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485310642550.png)

反面：

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485310659869.png)


----------


> 简单的评论一下这个得到的模型：
> 
> 下面不是很好，为什么不好呢。可能是因为圆环下面窄，中间宽，上面窄，所以开始打印的时候，是窄的，然后慢慢变宽。可能就是打印，从窄到宽这个过程，就得到的效果就不是很好。所以，就会出现现在得到的效果。
>  
> 但是上面非常好，就是从宽到窄的一个过程，打印机打印的非常好。
>  
> 所以，我推测，出现上面的下体打印效果差的原因可能有两个。
>  
> 1 . 可能是打印机打印从窄到宽的模型部分时，效果就比较差。这是无法修复的，属于打印机的与生俱来的毛病。
>  
> 2 . 也可能是因为，打印机打印接近底板地方的时候，打印的效果就是不怎么好。这个我们就可以修复它。
>  
> 对于可能性2，我们需要通过实验来验证是不是这个原因。所以，我们又做了一个模型。
>  
> 我们直接使用这个模型来验证：
> 
> ![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485330460807.png) 
> 
> ![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485330717421.png)
>  
> 经过了接近两个小时的打印，得到了最终的结果：
>  
> ![Alt text | 480x0](./1485390402045.png)
>  
> ![Alt text | 480x0](./1485390431885.png)
>  
> ![Alt text | 480x0](./1485390455275.png)
>  
> 从得到的结果，我们可以看到，从窄到宽的两个部分都不怎么好。
>  
> 所以，我猜测最可能的原因就是因为：我的模型不够“光滑”。



我重新设计一个模型：

这个模型，我分了很多面。（之前的只是横竖都是50个分面），现在是横竖都是255个分面。

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485391232182.png)

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485391327521.png)


----------

现在打印看看效果：

你可以从打印的效果，可以看出：跟之前没有什么却别。并没有任何效果的提升。

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485394881419.png)


----------

我们再打印一个模型：

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485403493320.png)


如果模型有问题，你可以把模型上传到下面这个网络里面，进行修复。

https://tools3d.azurewebsites.net/

![Alt text](/images/2017-2-18-3D-printer-experience-and-precautions-when-printing-large-models/1485449251335.png)


> 或者是 Windows 10系统里面自带的软件：**3D Builder** 软件进行修复。（我的电脑是Windows 10 的，所以，我比较习惯使用这个**3D Builder**软件来修复我使用SolidWorks软件设计好的模型。）

----------


## 解决问题：当打印从小面积到大面积的模型部分的时候出现的打印效果很差问题

解决办法就是：我现在习惯，不管我打印什么样的模型，我都习惯将模型倾斜45度角进行打印。这样可以有效的解决上面说的这个问题。
