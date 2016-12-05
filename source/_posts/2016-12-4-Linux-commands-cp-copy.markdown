---
layout: post
title: "Learning Linux 命令 001 cp 复制"
date: 2016-12-04 23:18:23 +0800
comments: true
sharing: true
categories: [Linux 命令]
tags: [cp, linux, 复制]
---

----


将单个文件 `file` 复制到指定目录`dir`里面：

```
cp file dir
```

> 当你使用`cp`命令的时候，如果出现下面的错误：
>  
> ```
> cp: omitting directory ‘file’
> ```
>  
> 说明：`file` 不是单个文件，是一个目录，你如果要复制目录，需要给`cp`命令加一个参数 `-r` 。

将目录 `dir1` 复制到 指定目录 `dir2` 里面：

```
cp -r dir1 dir2
```


