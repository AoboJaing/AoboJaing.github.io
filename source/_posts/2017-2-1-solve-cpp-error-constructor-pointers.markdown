---
layout: post
title: "C++ 构造函数使用`:成员变量(形参)`的形式给类里面成员变量赋值，如果成员变量和形参是指针，那么需要注意的事项"
date: 2017-2-1 00:38:20 +0800
comments: true
sharing: true
categories: [C++ error]
tags: [C++, C++ error]
---




----------

我先把结论列出来：

当成员变量和形参是指针，最好不要使用`:成员变量(形参)`这样的形式。因为你可以不是进行：`成员变量 = 形参`这个方向的赋值，你可能是执行：`形参 = 成员变量`这个方向的赋值。因为前提，它们都是指针嘛。

----------

## 今天我遇到了这样的一个错误：

下面的程序，编译是正常通过的，但是运行却不行。（我只是将相关的代码贴了出来）

```cpp
class PclView{
public:
    PclView(pcl::visualization::PCLVisualizer * &p);
    void showCloudsLeft(const pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_source,
                        const pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_target);
private:
    pcl::visualization::PCLVisualizer *p;
};
```

```cpp
PclView::PclView(pcl::visualization::PCLVisualizer * &p):p(p){
    vp_1 = 1;
    vp_2 = 2;
    // Create a PCLVisualizer object
    p = new pcl::visualization::PCLVisualizer ("Pairwise Incremental Registration example");
    p->createViewPort (0.0, 0, 0.5, 1.0, vp_1);
    p->createViewPort (0.5, 0, 1.0, 1.0, vp_2);
    p->removePointCloud ("vp1_target");
}

void PclView::showCloudsLeft(const pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_source,
                             const pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_target)
{
  p->removePointCloud ("vp1_target");
  p->removePointCloud ("vp1_source");

  pcl::visualization::PointCloudColorHandlerCustom<pcl::PointXYZ> tgt_h (cloud_target, 0, 255, 0);
  pcl::visualization::PointCloudColorHandlerCustom<pcl::PointXYZ> src_h (cloud_source, 255, 0, 0);
  p->addPointCloud (cloud_target, tgt_h, "vp1_target", vp_1);
  p->addPointCloud (cloud_source, src_h, "vp1_source", vp_1);

//  PCL_INFO ("Press Space to begin the registration.\n");
  p-> spinOnce();
}

```

当我们在`main.cpp`文件中定义了一个上面的类的实例化对象后，然后调用这个类的`showCloudsLeft()`方法。编译程序没有问题， 但是运行程序就会出现错误。

```cpp
int main(void){
	pcl::visualization::PCLVisualizer *p;
	PclView viewer(p);
	pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_source;
	pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_target;
	viewer.showCloudsLeft(cloud_source, cloud_target);
	return 0;
}
```

上面的程序运行的时候程序会死在`showCloudsLeft()`函数里面的`p->removePointCloud ("vp1_target");`这段代码。原因是：`p`指针为空。

----------


## 正确的写法：

问题出现在`PclView::PclView(pcl::visualization::PCLVisualizer * &p)`这个构造函数里面。

正确的写法有两种：

```cpp
PclView::PclView(pcl::visualization::PCLVisualizer * &p){
    this->p = p;
    vp_1 = 1;
    vp_2 = 2;
    // Create a PCLVisualizer object
    this->p = new pcl::visualization::PCLVisualizer ("Pairwise Incremental Registration example");
    this->p->createViewPort (0.0, 0, 0.5, 1.0, vp_1);
    this->p->createViewPort (0.5, 0, 1.0, 1.0, vp_2);
    this->p->removePointCloud ("vp1_target");
}
```

或者：

```cpp
PclView::PclView(pcl::visualization::PCLVisualizer * &p):p(p){
    vp_1 = 1;
    vp_2 = 2;
    // Create a PCLVisualizer object
    this->p = new pcl::visualization::PCLVisualizer ("Pairwise Incremental Registration example");
    this->p->createViewPort (0.0, 0, 0.5, 1.0, vp_1);
    this->p->createViewPort (0.5, 0, 1.0, 1.0, vp_2);
    this->p->removePointCloud ("vp1_target");
}
```


----------

现在问题就解决了。


----------

但是虽然现在的问题是解决了，但是程序还是有潜在问题的。（现在的程序，还没有达到我们想要的目的。）我们最开始设计这个构造函数，是想将外部通过形参传入的这个指针能够与这个实例化对象里面`pcl::visualization::PCLVisualizer * p`指针能够指向同一个东西，然后它们两个都可以去改变这个东西。

但是现在我们并没有做到这一点。我们可以使用下面的代码验证：

```cpp
int main(void){
	pcl::visualization::PCLVisualizer *p;
	PclView viewer(p);
	pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_source;
	pcl::PointCloud<pcl::PointXYZ>::Ptr &cloud_target;
	viewer.showCloudsLeft(cloud_source, cloud_target);
	p->removePointCloud ("vp1_target");
	return 0;
}
```

编译程序不会出现什么问题，但是现在运行，程序就会在`main()`函数里面的`p->removePointCloud ("vp1_target");`这段代码出现问题。


----------

所以，正真正确的解决办法是：

```cpp
PclView::PclView(pcl::visualization::PCLVisualizer * &p){
    vp_1 = 1;
    vp_2 = 2;
    // Create a PCLVisualizer object
    this->p = new pcl::visualization::PCLVisualizer ("Pairwise Incremental Registration example");
    this->p->createViewPort (0.0, 0, 0.5, 1.0, vp_1);
    this->p->createViewPort (0.5, 0, 1.0, 1.0, vp_2);
    this->p->removePointCloud ("vp1_target");
    p = this->p;
}
```

现在就变成了完美的程序，不会出现问题，也没有潜在的问题。

----------


## 出现上面的问题的原因

原因很简单，完美的设计思想是：希望两个指针都指向同一个存储空间，但是，实际上两个指针没有指向一个存储空间，一个指针指向了存储空间，而一个是空指针，所以就出现了错误。