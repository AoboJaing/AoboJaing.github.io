---
layout: post
title: "C# 001 --- 正确的删除一个控件的事件函数 --- 解决错误：	“A”不包含“B”的定义，并且找不到可接受类型为“A”的第一个参数的扩展方法“B”(是否缺少 using 指令或程序集引用?)"
date: 2016-11-13 13:54:49 +0800
comments: true
sharing: true
categories: [C#]
tags: [C#, 删除事件函数]
---


---

先添加一个控件。比如添加一个`GroupBox`控件。

![Alt text](/images/2016-11-13-cs-001-delete-event-function-resolve-error/1479014826968.png)


当然，这个控件你不需要任何事件函数，但是如果你已经双击这个控件，开始编辑这个控件的事件函数了，那么这个时候要删除这个控件的事件函数需要2步：

**Step 1 . ** 在 `Form11.cs` 文件中，将这个控件所有的事件函数删除。对于我们这个例子，删除的代码是：

```csharp
        private void groupBox1_Enter(object sender, EventArgs e)
        {

        }
```

如果这个时候，你运行程序会出错：

```
错误	1	“WindowsFormsApplication1_demo.Form1”不包含“groupBox1_Enter”的定义，并且找不到可接受类型为“WindowsFormsApplication1_demo.Form1”的第一个参数的扩展方法“groupBox1_Enter”(是否缺少 using 指令或程序集引用?)	
```

它提示你：你已经给`groupBox1`这个控件对象定义了一个`groupBox1_Enter`的方法了，但是编译器却没有找到这个函数。为什么没有找到？因为刚刚我们给它删除了。所以第2步：

**Step 2 . ** 在**解决方案资源管理器**，打开：`Form1.Designer.cs`文件：

![Alt text](/images/2016-11-13-cs-001-delete-event-function-resolve-error/1479015257166.png)

你会看到，一个小加号：

![Alt text](/images/2016-11-13-cs-001-delete-event-function-resolve-error/1479015310058.png)

点开这个小加号，里面就是所有空间的参数和方法的定义汇总。我们找到对应控件的事件函数：

![Alt text](/images/2016-11-13-cs-001-delete-event-function-resolve-error/1479015437616.png)

**VS** 软件已经将有错误的地方，用波浪线标注了。我们直接删除这一行，即可：

```csharp
            this.groupBox1.Enter += new System.EventHandler(this.groupBox1_Enter);
```

现在，再运行程序，就不会有错误了。



