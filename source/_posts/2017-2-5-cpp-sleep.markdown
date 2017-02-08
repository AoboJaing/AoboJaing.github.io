---
layout: post
title: "C++ 的延时函数"
date: 2017-02-05 01:32:23 +0800
comments: true
sharing: true
categories: [c++]
tags: [C++, 延时函数]
---


----------


## 方法一

在Linux下，我们这样使用：

```cpp
#include <iostream>
#include <unistd.h>

int main(void){
	while(1){
		std::cout << "Hello World!" << std::endl;
		sleep(1); //单位是秒
	}
	return 0;
}
```

我们使用`#include <unistd.h>`头文件里面的`sleep()`函数，给这个函数传入的形参是以秒为单位的正整数。


----------

上面的程序执行的效果应该是：以一秒为单位打印`Hello World!`这个字符串。


或者形参传入以微秒为单位（`1000,000`微秒 = `1`秒）的数据：

`usleep()`函数的详细介绍：[这里](http://pubs.opengroup.org/onlinepubs/007908799/xsh/usleep.html)。

```cpp
#include <iostream>
#include <unistd.h>

int main(void){
	while(1){
		std::cout << "Hello World!" << std::endl;
		usleep(1000000); //单位是微秒 1000000us = 1s
	}
	return 0;
}
```

----------

## 方法三

C++11里面，你可以这样使用：

我使用的是Qt5，在Qt5里面使用`C++11`，你需要在项目的`.pro`文件里面添加下面的这句代码：

```
CONFIG += c++11
```

> 如果你不在`.pro`文件中添加上面的这句代码，你就使用不了下面代码里面的`std::this_thread`。


```cpp
#include <iostream>
#include <chrono>
#include <thread>

int main(void){
	while(1){
		std::cout << "Hello World!" << std::endl;
		std::this_thread::sleep_for(std::chrono::milliseconds(1000)); //单位是毫秒
	}
	return 0;
}

```


----------

## 方法四

如果你使用了`Boost`库，那么你可以使用下面的代码实现延时的功能：

> Linux系统安装**Boost**库很简单，只需要执行：
> ```
> sudo apt-get install libboost-dev
> ```

我使用的是QT项目，所以我们需要在`.pro`文件中，添加`boost`库的头文件路径和链接文件的路径：

```
HEADERS += /usr/include/

LIBS += -L/usr/lib/x86_64-linux-gnu -lboost_system -lboost_thread
```

```cpp
#include <iostream>
#include <boost/thread/thread.hpp>

int main(void){
	while(1){
		std::cout << "Hello World!" << std::endl;
		boost::this_thread::sleep( boost::posix_time::milliseconds(1000) ); //单位是毫秒
	}
	return 0;
}

```

或者：

```cpp
boost::this_thread::sleep( boost::posix_time::seconds(1) ); //单位是秒
```


----------

参考网站：[Sleep for milliseconds](http://stackoverflow.com/questions/4184468/sleep-for-milliseconds)

