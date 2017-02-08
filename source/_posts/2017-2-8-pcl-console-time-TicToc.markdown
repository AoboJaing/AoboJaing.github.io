---
layout: post
title: "PCL 记录时间长度 — TicToc 类"
date: 2017-02-08 00:23:41 +0800
comments: true
sharing: true
categories: [PCL]
tags: [TicToc, 记录时间]
---


----------

对于PCL在**Windows**和**Linux**上的环境的搭建请参考我写的这几篇博客。


----------

```cpp
#include <pcl/console/time.h>
```
```
pcl::console::TicToc tt;
tt.tic ();

//需要记录执行多长时间的代码

std::cout << "[done, " << tt.toc () << " ms ]" << std::endl;
```

