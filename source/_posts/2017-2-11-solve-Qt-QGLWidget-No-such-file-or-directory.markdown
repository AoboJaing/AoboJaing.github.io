---
layout: post
title: "解决问题：QGLWidget：No such file or directory"
date: 2017-02-11 08:01:11 +0800
comments: true
sharing: true
categories: [Qt]
tags: [No such file or directory, Qt, Widget, GL]
---


----------

参考网站：[无法找到QT OpenGL QGLWidget](%E6%97%A0%E6%B3%95%E6%89%BE%E5%88%B0QT%20OpenGL%20QGLWidget)


----------

现在出现了这个问题：

```
QGLWidget: No such file or directory
```

![Alt text](/images/2017-2-11-solve-Qt-QGLWidget-No-such-file-or-directory/1486743476422.png)

## 解决办法

在`.pro`文件里面，添加：

```
QT += opengl
```

参考网站：[Qt OpenGL](http://doc.qt.io/qt-5/qtopengl-index.html#details)


