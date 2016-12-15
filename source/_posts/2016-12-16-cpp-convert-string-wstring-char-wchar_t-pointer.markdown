---
layout: post
title: "C++ string 、char 、char *、wstring、wchar_t * 、wchar_t 之间的转换"
date: 2016-12-16 07:28:48 +0800
comments: true
sharing: true
categories: [C++]
tags: [C++, string, wstring, char, wchar_t, char *, wchar_t *]
---


----------

## `char` 与 `wchar_t` 之间的转换

```cpp
#include <iostream>
#include <iomanip>

int main(void)
{
	char c = 'a';
	std::cout << c << std::endl;
	//char -> wchar_t
	wchar_t wc = (wchar_t)c;
	std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << wc << std::endl;
	//wchar_t -> char
	char c_ = (char)wc;
	std::cout << c_ << std::endl;
	
	system("pause");
	return 0;
}
```

输出：

```
a
U+0061
a
请按任意键继续. . .
```

> Unicode编码表：[A-Z,a-z,0-9的unicode编码表](http://blog.csdn.net/fedawn/article/details/7307993)

## `string` 与 `wstring` 之间的转换

```cpp
#include <iostream>
#include <string>
#include <iomanip>

int main(void)
{
	std::string str = "HelloWorld";
	std::cout << str << std::endl;
	//string -> wstring
	std::wstring wstr;
	wstr.assign(str.begin(), str.end());
	// std::cout << wstr.c_str() << std::endl; //error 这样是打印不出来的
	//std::cout << wstr.c_str() << std::endl; //error 编译不报错，但是它打印的是wstr第一个字符的地址
	//打印 success
	std::cout << "Unicode is ";
	for(int i=0; i<wstr.length(); i++){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << wstr[i] << " ";
	}
	std::cout << std::endl;
	//打印 end

	//wstring -> string
	std::string str_;
	str_.assign(wstr.begin(), wstr.end());
	std::cout << str_ << std::endl;

	system("pause");
	return 0;
}
```

输出：

```
HelloWorld
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
HelloWorld
请按任意键继续. . .
```

## `char *` 与 `string` 之间的转换

```cpp
#include <iostream>
#include <string>

int main(void)
{
	std::string str = "HelloWorld";
	//string -> char *
	char * cstr = (char *)str.c_str();
	std::cout << cstr << std::endl;
	//char * -> string
	std::string str_ = cstr;
	std::cout << str_ << std::endl;

	system("pause");
	return 0;
}
```

输出：

```
HelloWorld
HelloWorld
请按任意键继续. . .
```

## `char *` 与 `wchar_t *` 之间的转换

```cpp
#include <iostream>
#include <iomanip>

int main(void)
{
	char * cstr = "HelloWorld";
	std::cout << cstr << std::endl;

	// char * -> wchar_t *
	//wchar_t * wcstr = (wchar_t *)cstr; //error
	//success
	size_t len = strlen(cstr) + 1;
	size_t converted = 0;
	wchar_t *wcstr;
	wcstr=(wchar_t*)malloc(len*sizeof(wchar_t));
	mbstowcs_s(&converted, wcstr, len, cstr, _TRUNCATE);

	//打印
	wchar_t * temp = wcstr;
	int i = 0;
	std::cout << "Unicode is ";
	while(temp[i]!='\0'){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << temp[i] << " ";
		i++;
	}
	std::cout << std::endl;
	//打印 end

	std::cout << "------------------" << std::endl;
	//-------------------------------------------------

	wchar_t * wcstr_ = L"HelloWorld";
	//打印
	wchar_t * temp_ = wcstr_;
	int i_ = 0;
	std::cout << "Unicode is ";
	while(temp_[i_]!='\0'){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << temp_[i_] << " ";
		i_++;
	}
	std::cout << std::endl;
	//打印 end

	//wchar_t * -> char *
	size_t len_ = wcslen(wcstr_) + 1;
	size_t converted_ = 0;
	char * cstr_;
	cstr_ = (char*)malloc(len*sizeof(char));
	wcstombs_s(&converted_, cstr_, len_, wcstr_, _TRUNCATE);
	std::cout << cstr_ << std::endl;

	system("pause");
	return 0;
}
```

输出：

```
HelloWorld
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
------------------
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
HelloWorld
请按任意键继续. . .
```

> 注意：
>  
> * `cstr`、`wcstr`、`cstr_` 是地址变量，使用 `std::cout << cstr_ << std::endl;`代码打印的值是地址，并不是字符串的值。
> *  `wchar_t *` 与 `char *` 之间的转换，使用`wchar_t * wcstr = (wchar_t *)cstr;`是错误的。（异想天开）

## `wchar_t *` 与 `wstring` 之间的转换

```cpp
#include <iostream>
#include <string>
#include <iomanip>

int main(void)
{
	std::wstring wstr = L"HelloWorld";
	//打印
	std::cout << "Unicode is ";
	for(int i=0; i<wstr.length(); i++){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << wstr[i] << " ";
	}
	std::cout << std::endl;
	//打印 end
	//wstring -> wchar_t *
	wchar_t * wcstr = (wchar_t *)wstr.c_str();
	//打印
	wchar_t * temp = wcstr;
	int i = 0;
	std::cout << "Unicode is ";
	while(temp[i]!='\0'){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << temp[i] << " ";
		i++;
	}
	std::cout << std::endl;
	//打印 end
	//wchar_t * -> wstring
	std::wstring wstr_ = wcstr;
	//打印
	std::cout << "Unicode is ";
	for(int i=0; i<wstr_.length(); i++){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << wstr_[i] << " ";
	}
	std::cout << std::endl;
	//打印 end

	system("pause");
	return 0;
}
```

输出：

```
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
请按任意键继续. . .
```


----------

## `wchar_t *` 与 `string` 之间的转换

知道了上面的几种转换，我们就可以通过组合它们，来实现，比如：`wchar_t *` 与 `string` 之间的转换。

```cpp
#include <iostream>
#include <string>
#include <iomanip>

int main(void)
{
	std::wstring wstr = L"HelloWorld";
	wchar_t * wcstr = (wchar_t *)wstr.c_str();
	//打印
	wchar_t * temp = wcstr;
	int i = 0;
	std::cout << "Unicode is ";
	while(temp[i]!='\0'){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << temp[i] << " ";
		i++;
	}
	std::cout << std::endl;
	//打印 end

	//wchar_t * -> string (wchar_t * -> wstring -> string)
	std::wstring wstr_ = wcstr;
	std::string str;
	str.assign(wstr_.begin(), wstr_.end());
	std::cout << str << std::endl;
	//string -> wchar_t * (string -> wstring -> wchar_t *)
	wstr_.assign(str.begin(), str.end());
	wchar_t * wcstr_ = (wchar_t *)wstr_.c_str();
	//打印
	wchar_t * temp_ = wcstr;
	int i_ = 0;
	std::cout << "Unicode is ";
	while(temp_[i_]!='\0'){
		std::cout << "U+" << std::setw(4) << std::setfill('0') << std::hex << temp_[i_] << " ";
		i_++;
	}
	std::cout << std::endl;
	//打印 end

	system("pause");
	return 0;
}
```

输出：

```
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
HelloWorld
Unicode is U+0048 U+0065 U+006c U+006c U+006f U+0057 U+006f U+0072 U+006c U+0064
请按任意键继续. . .
```


----------


