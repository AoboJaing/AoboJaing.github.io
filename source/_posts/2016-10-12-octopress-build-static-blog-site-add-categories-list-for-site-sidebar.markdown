---
layout: post
title: "Octopress 搭建静态博客站点 --- 为站点侧边栏添加分类列表（Categories）"
date: 2016-10-12 16:15:13 +0800
comments: true
sharing: true
categories: [Use Octopress Build Blog Site]
tags: [Octopress]
---


---

一共三步，很简单。跟着走就可以。

---

**Step 1 . **  增加 `category_list` 插件

在 `octopress\plugins\` 文件夹里面，新建一个文件，取名为：`category_list_tag.rb`。并将下面的代码粘贴到里面。

```
module Jekyll
  class CategoryListTag < Liquid::Tag
    def render(context)
      html = ""
      categories = context.registers[:site].categories.keys
      categories.sort.each do |category|
        posts_in_category = context.registers[:site].categories[category].size
        category_dir = context.registers[:site].config['category_dir']
        category_url = File.join(category_dir, category.gsub(/_|\P{Word}/, '-').gsub(/-{2,}/, '-').downcase)
        html << "<li class='category'><a href='/#{category_url}/'>#{category} (#{posts_in_category})</a></li>\n"
      end
      html
    end
  end
end

Liquid::Template.register_tag('category_list', Jekyll::CategoryListTag)
```

这个插件会向`liquid`注册一个名为`category_list`的`tag`，该`tag`就是以`li`的形式将站点所有的`category`组织起来。如果要将`category`加入到侧边导航栏，需要增加一个`aside`。

---

**Step 2 . ** 增加 `aside`

在 `octopress\source\_includes\asides\` 文件夹里面，新建一个文件，取名为：`category_list.html` 。并粘贴下面的代码：

**注意：** 去掉 `%` 前面的 `\`。

```html
<section>
	<h1>Categories</h1>
	<ul id="categories">
		{\% category_list \%}
	</ul>
</section>
```

---

**Step 3 . ** 在 `_config.yml` 文件里面 ，修改 `default_asides` 项

打开 `octopress\_config.yml` 文件，修改里面的 `default_asides` 项，将 `asides/category_list.html` 添加进去。

```
default_asides: [asides/category_list.html, ......]
```

---

## 搞定

现在，我们执行 `rake generate` 命令来生成最新的博客站点。然后执行 `rake preview` 命令在本地预览博客站点。 看看修改后的效果。

![Alt text](/images/2016-10-12-octopress-build-static-blog-site-add-categories-list-for-site-sidebar/1476259852727.png)

---

---

参考网站：

为octopress添加分类(category)列表
http://codemacro.com/2012/07/18/add-category-list-to-octopress/