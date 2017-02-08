---
layout: post
title: "PCL 使用 pcl::visualization::PCLVisualizer 类里面的键盘事件方法 如何使用及需要注意的事项"
date: 2017-02-08 00:19:57 +0800
comments: true
sharing: true
categories: [PCL]
tags: [PCLVisualizer, PCL键盘事件, spinOnce(), registerKeyboardCallback()]
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

第二个：就是这个自定义的键盘事件函数了：`keyboardEventOccurred()`函数。想要让这个函数可以使用，我们必须要在程序中循环的调用`p->spinOnce()`方法，程序才能响应我们的这个键盘事件函数。

