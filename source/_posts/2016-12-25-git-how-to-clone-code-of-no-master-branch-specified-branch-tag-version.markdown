---
layout: post
title: "Git(GitHub) 003 如何 clone 非 master 分支的代码 — 切换到指定 branch分支 或者 tag版本"
date: 2016-12-25 14:44:29 +0800
comments: true
sharing: true
categories: [git_github]
tags: [git, branch, tag, 切换到指定分支, 切换到指定版本]
---


----------




----------



# 切换到指定 branch （分支）

----------

## 举例

我们的目的是：得到 https://github.com/turtlebot/turtlebot_viz 网址里面的**groovy**分支的源代码：

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482557635906.png)


第一步：git源代码到本地。（**注意：** 不是**Download ZIP**，它只是下载master分支的源代码，不会下载所有分支的源代码）

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482557660023.png)

```
git clone git@github.com:turtlebot/turtlebot_viz.git
```

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482557685824.png)

第二步：查看所有分支

> 1 . 绿色的表示本地当前分支
>  
>  2 . 红色的表示远程的分支。
>  
>  3 . `origin/HEAD -> origin/hydro` 指：远程库的当前分支是`hydro`
>   
>   ![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482647272808.png)


```
git branch -a
```

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482557771056.png)

第三步：切换到指定分支，比如**groovy**

```
git checkout groovy
```


----------

# 切换到指定 tag （版本）

##  举例

我们的目的是：得到 https://github.com/ros-drivers/freenect_stack 网址里面 **freenect-stack-0.2.2** 版本。

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482647506482.png)


克隆

```
git clone git@github.com:ros-drivers/freenect_stack.git
```

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482580629054.png)

```
cd freenect_stack
git tag
```

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482580655226.png)

```
git checkout freenect-stack-0.2.2
```

![Alt text](/images/2016-12-25-git-how-to-clone-code-of-no-master-branch-specified-branch-tag-version/1482580667832.png)

----------

> 总结：其实tag和 branch是一样的操作。

如果你感觉使用`git clone XXX` 下载源代码的速度太慢了，你可以参考[这篇博客](http://www.aobosir.com/blog/2016/12/25/git-config-agent-purpose-clone-download-speed-up/)来配置你的git，让它提速。


----------

参考网站：

* https://gaohaoyang.github.io/2016/07/07/git-clone-not-master-branch/
* http://www.jianshu.com/p/79cdb8d514ed
