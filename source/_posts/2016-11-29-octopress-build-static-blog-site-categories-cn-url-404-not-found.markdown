---
layout: post
title: "Octopress 搭建静态博客站点 — 让中文的分类列表（Categories）的超链接正常使用"
date: 2016-11-29 13:49:25 +0800
comments: true
sharing: true
categories: [use octopress build blog site]
tags: [Octopress, Categories, 404 Not Found, 中文错误]
---

---


## 前言

之前，我是按照我写的[这篇博客](http://www.aobosir.com/blog/2016/10/12/octopress-build-static-blog-site-add-categories-list-for-site-sidebar/)为**Octopress**站点侧边栏添加分类列表（Categories）。


----------


## 出现的问题

基于Octopress的博客系统自带了一个很好用分类目录插件。但遗憾的是它不支持中文链接URL，所以导致了：如果你分类列表有中文，那么点击的时候会链接到404页面。


----------


## 解决思路

中文取拼音。


----------


## 解决方法

参考网站：[解决Octopress分类目录支持中文的问题](http://jiankg.github.io/2014/10/16/jie-jue-octopressfen-lei-mu-lu-zhi-chi-zhong-wen-de-wen-ti/)

`/plugins/category_sidebar.rb` (若没有，自行创建)

```ruby
require 'stringex'

module Jekyll
  class CategoryListTag < Liquid::Tag
    def render(context)
      html = ""
      categories = context.registers[:site].categories.keys
      categories.sort.each do |category|
        posts_in_category = context.registers[:site].categories[category].size
        html << "<li class='category'><a href='/blog/categories/#{category.to_url.downcase}/'>#{category} (#{posts_in_category})</a></li>\n"
      end
      html
    end
  end
end

Liquid::Template.register_tag('category_sidebar', Jekyll::CategoryListTag)
```

## 搞定

现在你可以重新执行`rake generate`和`rake preview`、 `rake deploy`，分类列表中有中文字符的分类，就可以正常打开了，而实际的链接就是对应的拼音。


----------
