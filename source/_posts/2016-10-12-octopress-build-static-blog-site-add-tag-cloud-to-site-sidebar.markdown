---
layout: post
title: "Octopress 搭建静态博客站点 --- 为站点侧边栏添加标签云（Tag Cloud）"
date: 2016-10-12 +0800
comments: true
sharing: true
categories: [Use Octopress Build Blog Site]
tags: [Octopress, Tag Clud]
---


---

## 下载

首先到 https://github.com/robbyedwards/octopress-tag-pages 和 https://github.com/robbyedwards/octopress-tag-cloud clone这两个项目的代码。

	```
	$ git clone https://github.com/robbyedwards/octopress-tag-cloud.git
	$ git clone https://github.com/robbyedwards/octopress-tag-cloud.git
	```

---

## octopress-tag-pages

**Step 1 . ** 将 `octopress-tag-pages\plugins` 路径里面的 `tag_generator.rb` 文件复制到 `octopress\plugins\` 文件夹里面。

**Step 2 . ** 将 `octopress-tag-pages\source\_includes\custom` 路径里面的 `tag_feed.xml` 文件复制到 `octopress\source\_includes\custom\` 文件夹。

**Step 3 . ** 将 `octopress-tag-pages\source\_layouts` 路径里面的 `tag_index.html` 文件复制到 `octopress\source\_layouts\` 文件夹里。

---

## octopress-tag-cloud

**Step 1 . ** 将 `octopress-tag-cloud\plugins`  路径里面的 `tag_cloud.rb`  文件复制到 `octopress\plugins\`  文件夹里面。

**Step 2 . ** 将下面的代码复制到 `octopress\source\_includes\custom\asides\tags.html`。（这个文件需要你自己新建。）
**注意：** 先去掉 `%` 前面的反斜杠。

```
<section>
  <h1>Tags</h1>
  <ul class="tag-cloud">
    {\% tag_cloud font-size: 90-210%, limit: 15, style: para \%}
  </ul>
</section>
```

解释上面这段代码：

`tag_cloud` 的参数中。 `font-size` 指定 `tag` 的大小范围；`limit` 限定 `15` 个 `tag` ；`style :para` 指定不使用 `li` 来分割。

**Step 3 . **  

在 `octopress\_config.yml` 中的 `default_asides` 中添加 `custom/asides/tags.html`。
```
default_asides: [custom/asides/tags.html, .....]
```

---


现在执行 `rake generate` 生成博客。在使用 `rake preview` 在本地预览博客。

你会发现，在导航栏里面出现了 **Tags** 字段，但是里面没有标签。（不用担心，你已经成功添加了标签云。只不过你的博文里面没有标签，所以在标签云里面就没有标签。）

![Alt text](/images/2016-10-12-octopress-build-static-blog-site-add-tag-cloud-to-site-sidebar/1476209931221.png)


我们写一个带标签的博文。怎么写一个带标签的博文：

```
tags: [tag1, tag2, tag3]
```

![Alt text](/images/2016-10-12-octopress-build-static-blog-site-add-tag-cloud-to-site-sidebar/1476210344633.png)

---

执行 `rake generate` 命令时出现了问题：

![Alt text](/images/2016-10-12-octopress-build-static-blog-site-add-tag-cloud-to-site-sidebar/1476211427887.png)


## 解决：`comparison of Array with Array failed in _layouts/page.html` 错误

```
  Liquid Exception: comparison of Array with Array failed in _layouts/page.html
```

在 `octopress\plugins\tag_cloud.rb` 中第74行是这么写的:
```
if @limit > 0 and @sort != 'rand'
    # sort the tag pairs by frequency in descending order
    weighted.sort! { |a,b| b[1] <=> a[1] }
    # then slice off the top @limit tag pairs
    weighted = weighted[0,@limit]
end
```

`weighted = weighted[0,@limit]` 应该就是取指定数目的标签。如果你的标签数量少于 `@limit` ，那么就会报错。

所以我们修改第74行为:

```
      if @limit > 0 and @sort != 'rand' and @limit < weighted.length
```

同样的，将第95行修改为:

```
        if @limit > 0 and @limit < weighted.length
```

现在所有的修改都完成了，执行 `rake generate` 命令时，就不会再出现上面的错误了，但是现在却出现了下面的警告：

![Alt text](/images/2016-10-12-octopress-build-static-blog-site-add-tag-cloud-to-site-sidebar/1476211894282.png)

我们现在执行 `rake preview` 命令来预览看看。标签云是成功添加上去了:

![Alt text](/images/2016-10-12-octopress-build-static-blog-site-add-tag-cloud-to-site-sidebar/1476211997018.png)


## 解决 ` Build Warning: Layout 'nil' requested in tags/标签名/atom.xml does not exist.` 警告问题

将 `octopress\source\_includes\custom\tag_feed.xml` 文件里面 `nil` 改为 `null` ：

```
---
layout: null
---
```


搞定，现在再执行 `rake generate` 命令就不会出现这个警告了。不会出现任何问题。

## 搞定

---

---

参考网站：

(扩充)为 octopress 添加标签云：
http://yang3wei.github.io/blog/2013/01/30/zhuan-zai-wei-octopress-tian-jia-biao-qian-yun/
分类标签：
http://wiki.jikexueyuan.com/project/github-page/classification.html
在Octopress中添加标签：
http://devma.cn/blog/2016/04/02/zai-octopresszhong-tian-jia-biao-qian/

---

