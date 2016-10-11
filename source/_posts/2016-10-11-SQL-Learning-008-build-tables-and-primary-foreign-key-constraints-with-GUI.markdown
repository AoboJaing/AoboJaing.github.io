---
layout: post
title: "SQL 数据库 学习 008 如何通过图形化界面建表 和 建主外键约束"
date: 2016-10-11 23:49:40 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
---



---


在库里面建表。所以我们现在需要先新建一个库，然后在库里面新建一个表。

所以，先建一个 **库** ，取名为：`test`

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476180331922.png)

输入新建库的名字：`test` 。 现在点击 **确定** 按钮。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476180873442.png)

> 如果你在创建库的时候，遇到了下面这个异常。请查看[这篇博客](http://blog.csdn.net/u010800530/article/details/12093999)解决问题。
> 
> ![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476180567450.png)

新建成功：

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476180912977.png)

---

我们现在在库里面在建表。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476181053705.png)

建表的方式有两种：一种是鼠标点击的方式；一种是输入命令的方式。（但是不推荐鼠标去点。如果你想要这个命令正确的执行成功，并且它很稳定，一般都是使用命令去实现。）

---

现在我们先来介绍如何使用鼠标来操作：

## 下面使用点击鼠标的方式（图形化界面 ）进行建表：

对着 **库** 的 **表**  点击右击，点击 **表(T)...**

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476181347994.png)



![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476181423485.png)

**列** 名这里使用英文，后面选择 **数据类型** 。

目前第一个列取名为：`emp_ename` 。数据类型选择为：`nvarchar(MAX)` 。（表示的是：一个国际化编码可变的字符串。`n` 指的是：国际化，对汉字也支持；`var` 指的是：变量。所以：`nvarchar(MAX)` 指的是：可以存储汉字的字符串长度可以变化的字符串数据。）。后面的 `允许  Null 值`，如果你勾选了，意味着这一列的值可以是空的，所以我们不勾选。
其它**列**按照员工表对应的输入。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476181807481.png)

最终建出来的表就是下面这个样子的。（我们现在还没有添加 **部门编号**，为什么不添加？因为现在我们还没有部门这个表。（所以，如果我们先新建部门表，再建员工表就好了。））

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476181822333.png)

> `nchar` 中的 `n` 指的也是：支持国际化，支持汉字。

现在按 **Ctrl + S** 保存，将这个表取名为：`emp` 。 点击 **确定** 按钮。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476182492779.png)

现在这个 **员工** 表建立完成。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476182514880.png)

现在，我们就可以在：**对象资源管理器** 里面看到 **test**数据库里面的 **表** 选单里面多出来一个 `dbo.emp` 表。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476185855379.png)

> 如果你没有在这里面看到刚刚新建的 `dbo.emp` 表。进行下面的操作：（刷新一下，就出现了。）
>  
>  ![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476186193963.png)

展开 `dbo.emp` 表，你可以看到：

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476189999622.png)


现在还没有添加主键。（刚刚并没有设置主键。）如果没有主键，数据就容易 **冗余**。

举个例子：

在表中添加内容：

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476190370338.png)

如果添加的两条记录一模一样，那么得到的数据就 **冗余** 了。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476190501239.png)

> 如何添加记录？
> 
> 数据添加完之后，点击框框中的地方：
> 
> ![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476190612519.png)
> 
> 点击后，红色的叹号消失：
> 
> ![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476190654517.png)
> 
> 如果你添加的是冗余的数据，还有在点击执行按钮，叹号才会消失。
> 
> ![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476190697805.png)

在设计字段的时候，编号就是不能重复的，但是上面的两条冗余数据导致了编号的重复，所以现在编号就不能设置为主键了。不信，我们现在来试试。

对表的结构进行修改，点击 **设计**

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476190945148.png)

对 `emp_id` 属性 右键 ，选择 ：**设置主键(Y)**

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476190972850.png)

然后保存。（保存就会出错。）

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476191085152.png)

目前数据里面的 `emp_id` 属性有重复的数据，现在你又想将其设置为不可重复的主键，所以就出错了。

现在，我需要将表里面的 `emp_id` 属性里的数据进行修改。目的就是：不能让里面的数据内容重复。（我使用图形界面（就是鼠标点击）的方式修改不了表里面的数据；我们修改数据使用敲命令的方法也是修改不了的，这说明了：数据不能有冗余。）

我们现在只能将两条数据都删除。（使用图形界面（就是鼠标点击）的方式删除不了的；我们修改使用命令来删除）

新建一个查询文件（`.sql` 后缀的文件）。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476191767692.png)

在里面输入下面的命令：

```sql
delete from emp
```

点击 **执行** 按钮。

现在数据还在。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476192430675.png)

点击 **执行** 图标。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476192471479.png)

数据消失。（这个软件真是好弱啊！）

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476192510506.png)


---

折腾了一顿。

## 下面使用点击鼠标的方式（图形化界面 ）进行建主外键约束：

所以，我们应该先设置主键，然后 `Ctrl + S` 保存。接下来在添加数据。这才是正确的步骤。

接着添加，数据：


![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476192873680.png)

现在有了主键，导致了：主键里面的数据不能一样。


---

现在，我们在写一个表： **部门表** 。并添加下面的数据，同时将 `dept_id` 属性设置为 **主键**。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476195050064.png)

按 `Ctrl + S` 保存此表，命名为：`dept` 

> 注意：数据是中文的无所谓。但是你不要把表的结构和库的结构也写成中文。

现在我们来到 **emp** 表。添加 `dept_id` 这个属性（注意：这个属性的 `允许Null值`要勾选）。（目的是：将其设置为**外键**）

然后右键，点击 **关系**

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476197842775.png)

然后点击 **添加**

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476197065843.png)

点击 下面红框框里面的按钮。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476197186532.png)

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476197233271.png)

设置为下面这个样子。将 `dept_id` 这个属性设置为 **外键**。

解释一下：存在外键的表叫做 **外键表**，（**外键**：就是来自于另外一个表的**主键**）。 `emp`（员工） 表里面有一个`dept_id` （部门编号）这个外键，它就是 `dept` （部门）表的主键。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476197347119.png)


点击 **确定**， 再点击 **关闭**。现在按 `Ctrl + S` 保存，会弹出下面的窗口。点击 **是** 按钮。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476197679992.png)

---

我现在在 `dept` （部门）表里面添加数据。

![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476198258461.png)


现在再来到 `emp` （员工）表里面，给`dept_id`（部门编号）（外键） 添加数据。（如果你打开`emp`表发现里面现在还没有`dept_id`这个属性，就关闭这个页面，重新打开这个`emp`表，就有了。（这个软件正弱！））


![Alt text](/images/2016-10-11-SQL-Learning-008-How-to-build-tables-and-build-primary-foreign-key-constraints-through-graphical-interface/1476198701835.png)

---

---

我们来**总结**一下：应该先建部门表，然后在建员工表，是最好的。也就是说：先建**主键表**，然后再将**外键表**（因为**外键表**有数据来自另外的表（**主键表**））。




