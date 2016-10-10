---
layout: post
title: "Octopress 搭建静态博客站点 --- 自定义字体设置"
date: 2016-10-10 10:04:40 +0800
comments: true
sharing: true
categories: [Use Octopress Build Blog Site]
---



---

字体配置文件在 `octopress/sass/custom/` 文件里面：`_fonts.scss` 文件。

![Alt text](/images/2016-10-10-use-octopress-build-blog-site-custom-fonts/1476063413831.png)

默认情况下字体配置都是被注释掉的。我们将注释都去掉。

```
$sans: "Optima", sans-serif;
$serif: "Baskerville", serif;
$mono: "Courier", monospace;
$heading-font-family: "Verdana", sans-serif;
$header-title-font-family: "Futura", sans-serif;
$header-subtitle-font-family: "Futura", sans-serif;
```

> 引号里面的是：**字体名**。后面跟的是：`sans-serif`(无衬线字体)、`serif`（衬线）、`monospace`（等宽字体）。

* `$sans`：定义的是无衬线正文的字体 
	* ![Alt text](/images/2016-10-10-use-octopress-build-blog-site-custom-fonts/1476063715659.png)
* `$serif`：定义的是衬线正文的字体
* `$mono`：定义的是代码的字体
* `$heading-font-family`：定义的是文章标题的字体
* `$header-title-font-family`：定义的是博客标题的字体
* `$header-subtitle-font-family`：定义的是博客子标题的字体

我将它们修改为下面这样的配置。（就是将所有的字体都设置为：`Comic Sans MS`）

```
$sans: "Comic Sans MS", sans-serif;
$serif: "Comic Sans MS", serif;
$mono: "Comic Sans MS", monospace;
$heading-font-family: "Comic Sans MS", sans-serif;
$header-title-font-family: "Comic Sans MS", sans-serif;
$header-subtitle-font-family: "Comic Sans MS", sans-serif;
```

现在执行 `rake generate` 命令生成博客站点。在执行 `rake preview` 命令在本地开设4000端口。在浏览器中浏览 `localhost:4000` 端口进行预览。（效果不错。）

![Alt text](/images/2016-10-10-use-octopress-build-blog-site-custom-fonts/1476064562554.png)

![Alt text](/images/2016-10-10-use-octopress-build-blog-site-custom-fonts/1476064543308.png)


---

参考网站：
利用Octopress和Github搭建个人博客（四）：自定义字体
[http://glgjing.github.io/blog/2015/01/31/li-yong-octopresshe-githubda-jian-ge-ren-bo-ke-(si-):zi-ding-yi-zi-ti/](http://glgjing.github.io/blog/2015/01/31/li-yong-octopresshe-githubda-jian-ge-ren-bo-ke-%28si-%29:zi-ding-yi-zi-ti/)

