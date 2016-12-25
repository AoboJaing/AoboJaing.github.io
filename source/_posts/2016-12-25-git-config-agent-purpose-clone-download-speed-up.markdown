---
layout: post
title: "Git(GitHub) 004 配置代理 目的：clone提速"
date: 2016-12-25 15:08:25 +0800
comments: true
sharing: true
categories: [git_github]
tags: [git, config, clone, git 提速, git 代理]
---

----------


> 你如果没有翻墙，就算通过本篇博客对你的Git进行了配置，也是没有一点效果的。

在终端中执行：

```
$ git config --global http.proxy http://127.0.0.1:1080
$ git config --global https.proxy https://127.0.0.1:1080
```

查看一下：

```
$ git config --list
```

对于我现在使用的Windows 系统而言，输出是下面这个样子的。

```
core.symlinks=false
core.autocrlf=true
core.fscache=true
color.diff=auto
color.status=auto
color.branch=auto
color.interactive=true
help.format=html
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
diff.astextplain.textconv=astextplain
rebase.autosquash=true
credential.helper=manager
filter.lfs.clean=git-lfs clean %f
filter.lfs.smudge=git-lfs smudge %f
filter.lfs.required=true
user.name=AoboJaing
user.email=744910955@qq.com
https.proxy=https://127.0.0.1:1080
http.proxy=http://127.0.0.1:1080
```


----------


现在测试下载一个源代码试试看：（速度马上提上来）

![Alt text](/images/2016-12-25-git-config-agent-purpose-clone-download-speed-up/1482559985250.png)

## 搞定

----------

## **注意：** 错误的做法：

```
$ git config --global http.proxy 'socks5://127.0.0.1:1080'
$ git config --global https.proxy 'socks5://127.0.0.1:1080'
```


----------

参考网站：

* https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE
* https://gist.github.com/laispace/666dd7b27e9116faece6
