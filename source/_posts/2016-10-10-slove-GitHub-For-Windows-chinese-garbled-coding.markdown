---
layout: post
title: "解决 GitHub For Windows 客户端软件中代码的中文显示乱码问题"
date: 2016-10-10 07:47:34 +0800
comments: true
sharing: true
categories: [Git/GitHub]
---


---

`README.md` 文件里面是有中文的。在 `GitHub For Windows` 客户端软件里面显示中文是乱码的。

![Alt text](/images/2016-10-10-slove-GitHub-For-Windows-chinese-garbled-coding/1476055346118.png)

解决办法：

**Step 1 . ** 将 `README.md` 文件使用 **Notepad++** 软件打开。
（如果你的电脑上没有 **Notepad++** 软件，你可以参考[这篇博客](http://www.aobosir.com/blog/2016/10/10/Windows-install-Notepad++/)来下载安装它。）

**Step 2 . ** 选择： **格式** -> **转为 Utf-8 无 BOM 编码格式**

**Step 3 . ** 保存 `README.md` 文件

**Step 4 . ** 将修改重新推送到 **GitHub** 远程。

问题解决：

![Alt text](/images/2016-10-10-slove-GitHub-For-Windows-chinese-garbled-coding/1476055880353.png)




---


> **GitHub For Windows ** 客户端软件是一个非常好的软件，它实现了：即使你不会 `git` 命令行工具的时候，一样可以使用 **GitHub For Windows ** 客户端软件里面简单点的点击按钮就可以一样将代码推送到 **GitHub** 远程。

---

> 下载、安装、配置 **GitHub For Windows ** 客户端软件的图文教程可以参考这篇博客。

---

> 因为 **GitHub** 在推送代码到远程的时候，会自动将所有文件的编码方式转换为 `UTF-8` ，所有在网页里面浏览你的 **GitHub** 仓库的时候，中文是不会出现乱码的。
> 但是在本地，要想在 **GitHub For Windows** 客户端软件里面也能正常看到 中文，而不是乱码，就要自己手动的将含有中文的文件转换为：`UTF-8`编码方法。（如果是 **Windows** 系统就要转为：`Utf-8 无 BOM` 编码格式）