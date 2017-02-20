---
layout: post
title: "解决 -bash:  catin_make:  command not found 问题"
date: 2017-02-21 04:08:00 +0800
comments: true
sharing: true
categories: [ROS]
tags: [ROS, catkin_make, command not found]
---


----------


* 当前使用的ROS 版本：Groovy


----------

```
ubuntu@ubuntu:~/catkin_ws$ catin_make
-bash: catin_make: command not found
```

## 问题出现的原因

参考网站：http://answers.ros.org/question/212492/catkin_make-command-not-found/

先来查看当前ROS的环境变量：

```
cat ~/.bashrc
```

![Alt text](/images/2017-2-21-solve-bash-catin_make-command-not-found/1482563988992.png)



我们发现里面已经有`source /opt/ros/indigo/setup.bash`这行代码了。（如果没有一定要添加上。）

为什么还是出现问题呢。


----------

后来我才发现，出现错误的原因：

是因为我输错`catin_make`

正确的命令是：

```
catkin_make
```
