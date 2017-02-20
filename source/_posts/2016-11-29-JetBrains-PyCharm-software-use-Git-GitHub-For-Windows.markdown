---
layout: post
title: "在 JetBrains PyCharm 软件上使用 Git(Github) --- 如何使用GitHub For Windows软件的GUI界面给一个代码库添加一个`.gitignore`文件 --- 创建一个GitHub远程代码库的完整步骤"
date: 2016-11-29 11:44:46 +0800
comments: true
sharing: true
categories: [git_github]
tags: [PyCharm, Windows, Git, Github, 软件使用]
---

---

* 我的电脑：Windows 10 64位
* PyCharm 软件的版本：PyCharm 2016.1.4
* Git For Windows版本：Git-2.10.0-64-bit
* GitHub For Windows软件版：GitHub For Windows 3.0.5.2


----------

参考网站：[How to Use PyCharm with Github](https://www.youtube.com/watch?v=bsN7ogDz02g)

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480361358084.png)


----------

在 JetBrains PyCharm 软件上使用 Git(Github)，开发项目时，推送代码修改到远程库会变得更加便捷。


----------


## 准备工作

你的电脑里面需要有的软件：

* Git For Windows
* GitHub For Windows
* JetBrains PyCharm

你可以到这里查看如何下载和安装这些软件的图文教程：

* [Git For Windows 和 GitHub For Windows 这两个软件的下载和安装的教程](http://www.aobosir.com/blog/2016/11/29/Git-GitHub-001-For-Windows-download-install-tutorial/)
* [PyCharm 软件的下载、安装、破解教程](http://www.aobosir.com/blog/2016/11/29/PyCharm-software-professional-download-install-Crack-Registration/)


----------

## 在 JetBrains PyCharm 软件上使用 Git(Github)

对于已有项目文件夹，

**Step 1 . ** 在文件夹里面打开命令行，执行 `git init` 命令，将这个项目文件夹做成本地库。

**Step 2 . ** 使用**GitHub For Windows** 软件克隆本地库，忽略一些文件，并上传到GitHub远程。

具体详细的步骤如下：

克隆本地库：

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480384008856.png)

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480384665342.png)

添加`ignorefile` 文件

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480384713963.png)

点击 **+ Add a default .gitignore file.** 按钮

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480386549071.png)

我们这个项目使用的开发软件是 **JetBrains PyCharm** 软件，所以我们需要写一个符合 **JetBrains PyCharm** 软件 的 `.gitignore` 文件。

其实我们不需要自己写 `.gitignore` 文件，GitHub 官方已经为我们写好很多的  `.gitignore` 文件。

点击 **example**：

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480386671756.png)

弹出一个网页，将里面的`gitignore/Global/JetBrains.gitignore` 的内容复制粘贴：

（我们再在里面添加一行：`.idea/*`）

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480387492001.png)

现在，直接点击 `OK` 就可以了。

现在，你可以发现，只有3个改变的文件了：（这是因为一些文件被忽略，不需要上传到远程。）

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480387512124.png)

输入 **Summary** 和 **Description** ，点击 **Commit to master** 按钮将修改提交到指定分支上（当前指定分支是：`master`）。

最后点击 **Publish** 按钮，推送到远程库。

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480387792020.png)

第一次推送，需要填写下面的信息。注意：`Name` 默认不变；`Description` 里面输入好描述信息（中英文都可以）。

同时选中好要推送到的GitHub账号。

填好之后点击 **Pubish xxx** 按钮。（可能会失败，白天可能是因为GitHub官网服务器的原因，晚上会好一点。解决办法就是：多试几次。）

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480387921240.png)


**Step 3 . ** 使用 **PyCharm** 软件打开看看那个python项目。

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480388438196.png)

你会看到：

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480388544163.png)


**Step 4 . ** 当你对项目进行增减代码后，你想要将修改推送到远程库时。

方法1 ： 就点击上图中红圈里面的图标。然后进行推送。

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480388727382.png)

方法2 ： 你也可以使用 **GitHub For Windows** 软件进行推送。

（推送方法：输入 **Summary** 和 **Description** ，点击 **Commit to master** 按钮将修改提交到指定分支上（当前指定分支是：`master`）。最后点击 **Sync** 按钮，推送到远程库。）

![Alt text](/images/2016-11-29-JetBrains-PyCharm-software-use-Git-GitHub-For-Windows/1480388817420.png)

> 两个方法互不干扰，你使用了其中任意一种方法推送了修改，那么另外一种方法里面也好显示推送完成，没有修改的文件了。
