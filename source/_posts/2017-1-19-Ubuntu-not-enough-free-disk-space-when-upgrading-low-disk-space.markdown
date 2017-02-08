---
layout: post
title: "Ubuntu 解决更新软件包的时候出现的 “Low Disk Space” 存储空间不足问题"
date: 2017-01-19 17:15:24 +0800
comments: true
sharing: true
categories: [linux]
tags: [Ubuntu, Low Disk Space, Not enough disk space]
---


----------
当你的Ubuntu系统的真机或者虚拟机使用时间长了，安装下载的软件包多了。同时你的电脑的存储空间本身又不多。这样，时间一长，就会出现下面的这个问题：


![Alt text](/images/2017-1-19-Ubuntu-not-enough-free-disk-space-when-upgrading-low-disk-space/1484814879456.png)

系统提示你：现在系统的存储空间已经快要用没有了。

> 我现在这个情况，我这个Ubuntu系统是安装在一个虚拟机里面的，我只是给它分配了20G的硬盘空间。所以，我使用了大约2个月的时间，就出现了存储空间不足的问题。

下面就来解决这个问题。

其实解决这个问题很简单。我们只需要清理一下系统就可以。

参考网站：http://askubuntu.com/questions/298487/not-enough-free-disk-space-when-upgrading

你需要安装一个**ubuntu-tweak**软件，具体步骤如下：（如果你的Ubuntu里面有，就可以跳过这一步）

```
$ sudo add-apt-repository ppa:tualatrix/ppa
$ sudo apt-get update
$ sudo apt-get install ubuntu-tweak
```


现在启动ubuntu-tweak软件，进行清除缓存： 

```
$ ubuntu-tweak
```

![Alt text](/images/2017-1-19-Ubuntu-not-enough-free-disk-space-when-upgrading-low-disk-space/1484815204113.png)

然后切换到"Janitor"标签，选择你要清除的Apps、Personal、System的复选框，然后点击"Clean"按钮进行清除。

![Alt text](/images/2017-1-19-Ubuntu-not-enough-free-disk-space-when-upgrading-low-disk-space/1484815455240.png)

它这里面删除的是：比如， 我们下载的安装包，删除的就是这些安装包。

![Alt text](/images/2017-1-19-Ubuntu-not-enough-free-disk-space-when-upgrading-low-disk-space/1484816863268.png)

Over 2016-5-11 16:38:02
