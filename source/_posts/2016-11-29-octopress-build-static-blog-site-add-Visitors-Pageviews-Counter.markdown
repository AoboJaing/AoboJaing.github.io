---
layout: post
title: "Octopress 搭建静态博客站点 --- 添加访客统计"
date: 2016-11-29 13:26:33 +0800
comments: true
sharing: true
categories: [use octopress build blog site]
tags: [Octopress, 访客统计, Flag Counter, Liquid Exception]
---

---

参考网站：[Octopress博客的个性化配置：添加访客统计](http://tianweili.github.io/blog/2015/01/11/setup-octopress-blog/#h28)

----------

**Step 1 . ** 本博客的访客统计系统使用的是**Flag Counter**，所以要先去[**Flag Counter**](http://www.flagcounter.com/)获取代码。

**Step 2 . ** 拿到代码后添加`.\source\_includes\custom\asides\flag_counter.html`文件：

```
<section>
  <h1>访客统计</h1>
  <br/>
  <a href="http://s07.flagcounter.com/more/2SH"><img src="http://s07.flagcounter.com/count/2SH/bg_FFFFFF/txt_000000/border_CCCCCC/columns_2/maxflags_12/viewers_0/labels_0/pageviews_1/flags_0/" alt="Flag Counter" border="0"></a>
</section>
```

**Step 3 . ** 将页面添加到侧边栏，在`./_config.yml`配置文件中添加下面一行配置：

```
default_asides: [……, custom/asides/flag_counter.html]
```

**Step 4 . ** 最后添加控制开关，在`./_config.yml`配置文件中添加下面一行配置：

```
# Flag Counter
flag_counter: true
```

## 搞定

----------


现在执行 `rake generate` 来生成博客站点。

> 如果你在执行这一步的时候不到了下面这个问题：
>  
> ```
>   Liquid Exception: invalid byte sequence in UTF-8 in _layouts/page.html
> jekyll 2.5.3 | Error:  invalid byte sequence in UTF-8
> ```
>  
> ![Alt text](/images/2016-11-29-octopress-build-static-blog-site-add-Visitors-Pageviews-Counter/1480394392417.png)
>  
> 解决办法：
>  
> `.\source\_includes\custom\asides\flag_counter.html` 文件使用 [**Notepad++** 软件](http://www.aobosir.com/blog/2016/10/10/Windows-install-Notepad++/) 转换为UTF-8无BOM编码格式，即可解决问题。
>  
> ![Alt text](/images/2016-11-29-octopress-build-static-blog-site-add-Visitors-Pageviews-Counter/1480394475393.png)



