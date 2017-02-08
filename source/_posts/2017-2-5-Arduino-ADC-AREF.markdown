---
layout: post
title: "Arduino 005 ADC"
date: 2017-02-05 16:38:21 +0800
comments: true
sharing: true
categories: [Arduino]
tags: [Arduino, ADC, AREF, analogRead(pin), analogReference(type)]
---


----------

我使用的Arduino板子是：Arduino UNO R3 （[这里](http://www.aobosir.com/blog/2017/02/05/Arduino-UNO-R3-pin-definition/) 关于这个板子的引脚介绍。）

参考文献：《Arduino程序设计基础》 3.4 设置ADC参考电压


----------

好的，现在我们知道使用`analogRead()`函数来获取模拟输入口的电压。

![Alt text](/images/2017-2-5-Arduino-ADC-AREF/1486283071912.png)


## 设置参考电压

Arduino板子上有一个引脚：**AREF** 引脚，它就是用来连接参考电压的。如果我们没有设置参考电压的话，Arduino会默认使用工作电压作为参考电压。工作电压一般都是5V，所以默认的参考电压也为5V。

如果我们给Arduino的ADC设置参考电压，除了上面我们说的：要在Arduino板子上的**AREF**引脚上给一个参考电压外，我们可以还需要在程序初始化的地方使用`analogReference()`函数来设置Arduino使用外部参考电压。

![Alt text](/images/2017-2-5-Arduino-ADC-AREF/1486283448260.png)


----------

## 设置参考电压是需要注意

如果你要设置参考电压，注意：这个电压必须大于0，并且小于当前的工作电压（Arduino的工作电压一般为5V），否则可能会损坏Arduino控制器。


----------



