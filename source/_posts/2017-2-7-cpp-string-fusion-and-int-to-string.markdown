---
layout: post
title: "C++ 字符串融合 和 string 与 int 之间最简单的转换方法"
date: 2017-02-07 16:40:16 +0800
comments: true
sharing: true
categories: [C++]
tags: [C++, C++11, string与int之间的转换,字符串融合]
---


----------

## 字符串融合

```cpp
#include <string>

std::string str = std::string("../pairAlginClass/capture0001") + std::string(".pcd");
或者
std::string str(std::string("../pairAlginClass/capture0001") + std::string(".pcd"));
```


----------

## string 与 int 之间最简单的转换方法

下面的代码，我们需要使用**C++11**，**C++11**里面有`std::to_string()`方法。

```cpp
#include <string>

int i = 123;
std::string str = std::to_string(i);
```

## 给项目添加**C++11**：

如果是`CMakeLists.txt`文件的项目。就在`CMakeLists.txt`文件中添加：

```cmake
cmake_minimum_required(VERSION 2.8)
set(CMAKE_CXX_STANDARD 11)
```

如果是`Qt`项目的，就在`.pro`文件里面添加：

```
CONFIG += c++11
```


----------

参考网站：

* [在C ++中将int转换为字符串的最简单的方法](http://stackoverflow.com/questions/5590381/easiest-way-to-convert-int-to-string-in-c)
* [如何激活C ++ 11在CMake？](http://stackoverflow.com/questions/10851247/how-to-activate-c-11-in-cmake)

