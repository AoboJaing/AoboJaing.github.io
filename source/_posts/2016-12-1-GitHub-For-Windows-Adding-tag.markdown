---
layout: post
title: "Git(GitHub) 002 如何在GitHub For Windows 软件上为代码库创建一个版本标签"
date: 2016-12-01 08:04:17 +0800
comments: true
sharing: true
categories: [git_github]
tags: [GitHub For Windows, Git, tag]
---

---

参考网站：

* [git 创建标签](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951758572072ce1dc172b4178b910d31bc7521ee4000)
* [git 操作标签](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951885068a0ac7d81c3a64912b35a59b58a1d926b000)
* [Github for Windows - Adding tags](http://stackoverflow.com/questions/13862517/github-for-windows-adding-tags)


----------

要想给代码库贴标签，Github For Windows 软件上没没有这个按钮。你需要在Github For Windows 软件上打开 **Git 命令行窗口**，还是要使用命令行工具来完成这个工作。

![Alt text](/images/2016-12-1-GitHub-For-Windows-Adding-tag/1480548346142.png)

```
git tag -a v1.0 -m "description information"
git push origin v1.0
```


----------

当你执行完`git tag -a v1.0 -m "description information"`，想要查看一下，你可以执行：

```
git show v1.0
```

如果你执行完`git tag -a v1.0 -m "description information"`，想要删除这个标签，可以执行：

```
git tag -d v1.0
```


----------
