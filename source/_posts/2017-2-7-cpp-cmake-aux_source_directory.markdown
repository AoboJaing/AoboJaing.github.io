---
layout: post
title: "C++ 编写类文件的时候，需要注意的问题"
date: 2017-02-07 00:13:15 +0800
comments: true
sharing: true
categories: [C++]
tags: [C++, CMake, aux_source_directory()]
---


----------

一段时间不编写程序了，基本上都忘记了。今天我来介绍一下：当我们编写类文件的时候，需要注意的问题：


----------

比如，我现在写了`pairAlgin.hpp`文件 和 `pairAlgin.cpp`文件。

我在`pairAlign.hpp`文件里面

```cpp
class PairAlign{
public:
	PairAlign();
};
```

你会发现：这个文件的名字和里面的类的名字不同。一个是`pairAlign`的文件名，一个是`PairAlign`类。这是没有关系的。这个随便。


----------

但是，我在使用`make`命令编译程序的时候，上面没有错误的程序竟然编译不了。

后来，我们知道了问题。其实是我们的`CMakeLists.txt`文件里面的问题。因为 `pairAlgin.hpp`文件 和 `pairAlgin.cpp`文件是放在`pairAlgin`文件夹里面的。而我却没有将这个文件夹添加的被编译的`SRC_LIST`变量里面。

我们需要在`CMakeLists.txt`文件里面的`aux_source_directory(. SRC_LIST)`下面添加下面这个代码，就可以解决问题：

```cmake
aux_source_directory(./pairAlign/ SRC_LIST)
```


----------

现在我们在重新执行：

```
cmake ..
make
```

就可以编译成功了。
