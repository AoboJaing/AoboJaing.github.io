---
layout: post
title: "PCL 使用 pcl::visualization::PCLVisualizer 类里面的键盘事件方法 如何使用及需要注意的事项"
date: 2017-02-08 14:16:42 +0800
comments: true
sharing: true
categories: [PCL]
tags: [PCLVisualizer, PCL键盘事件, spinOnce(), registerKeyboardCallback(), sleep]
---


----------

## 如何使用 pcl 库里面的可视化模块的键盘事件

```
#include <pcl/visualization/pcl_visualizer.h>

bool iteration_flag = false;

void keyboardEventOccurred(const pcl::visualization::KeyboardEvent& event, void* nothing){
	if(event.getKeySym() == "space" && event.keyDown()){
		iteration_flag = true;
	}
}

int main(){
	pcl::visualization::PCLVisualizer *p;
	p = new pcl::visualization::PCLVisualizer("PCL Windows");
	p->registerKeyboardCallback(&keyboardEventOccurred, (void*)NULL);
	
	while(iteration_flag != true){
		p->spinOnce();
	}
	return 0;
}

```


----------

## 需要注意的事项：

第一个：就是，你定义的这个`p`指针，必须要给它赋值实例化对象：`p = new pcl::visualization::PCLVisualizer("PCL Windows");`，否则程序编译不会出现错误，但是运行的时候会出现内存异常的运行错误。


----------

第二个：就是这个自定义的键盘事件函数了：`keyboardEventOccurred()`函数。想要让这个函数可以使用，我们不需要再程序中循环的调用`p->spinOnce()`方法，程序才能响应我们的这个键盘事件函数。


----------

第三个：一个也非常重要：其实上面的代码中，这段程序是不安全的：

```cpp
	while(iteration_flag != true){
		p->spinOnce();
	}
```

因为如何程序在这个地方一直的执行，如果你可视化的是一个点比较多的点云，那么一段时间后（大约不到5秒钟），你的电脑就会卡得要死！！！！


安全的程序应该是下面这个样子的：（参考网站：[这里](http://pointclouds.org/documentation/tutorials/pcl_visualizer.php#pcl-visualizer)）

我们添加延时函数，不让它一直执行`spinOnce()`方法。

```cpp
#include <boost/thread/thread.hpp>
```

```cpp
  while (iteration_flag != true)
  {
    p->spinOnce (100);
    boost::this_thread::sleep (boost::posix_time::microseconds (100000));
  }
```

其中[`spinOnce()`函数](http://docs.pointclouds.org/trunk/classpcl_1_1visualization_1_1_p_c_l_visualizer.html#a896556f91ba6b45b12a9543a2b397193)里面的`100`指的是：**How long (in ms) should the visualization loop be allowed to run.**

![Alt text](/images/2017-2-8-pcl-visualization-PCLVisualizer-register-keyboard-callback/1486533744923.png)


其中的`boost::this_thread::sleep (boost::posix_time::microseconds (100000));`是延时100000微秒，也就是0.1秒。

