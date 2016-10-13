---
layout: post
title: "SQL 数据库 学习 010 表和约束的区别、check约束、default约束、unique约束、not null约束"
date: 2016-10-13 12:40:11 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

## 表和约束的区别

* 数据库是通过表来解决事物的存储问题的。
* 数据库是用过约束来解决事物取值的有效性和合法性的问题。
* 建表的过程就是指定事物属性及其事物属性各种约束的过程。

---

## check 约束

意义：保证事物属性的取值在合法的范围之内。


我们先创建一个表：（建表之前，先确保选中了指定的库）

![Alt text](/images/2016-10-13-SQL-Learning-010-differences-tables-contraints-check-default-unique-not-null/1476251551513.png)

点击 **新建查询** 按钮。输入下面的指令来新建一个带有`check` 约束的学生表：

```sql
create table student
(
	stu_id int primary key,
	stu_sal int check (stu_sal>=1000 and stu_sal<=8000)
)
```

现在，选中，然后点击执行。

现在刷新右侧栏`test`库的 **表** ，就可以看到刚刚建的学生表：

![Alt text](/images/2016-10-13-SQL-Learning-010-differences-tables-contraints-check-default-unique-not-null/1476251700453.png)


接下来是，向这个表里面插数据：

```
insert into student values (1, 1000)
insert into student values (2, 10000)
```


> 这就是所谓的第4代语言。全都是命令，你不需要知道它里面是如何实现的。这就是第4代编程语言。


现在`student(2)` 的工资已经超出了约束。如果你现在选中这两行命令。点击 **执行**，就会出现错误。

```
消息 547，级别 16，状态 0，第 8 行
INSERT 语句与 CHECK 约束"CK__student__stu_sal__1A14E395"冲突。该冲突发生于数据库"test"，表"dbo.student", column 'stu_sal'。
语句已终止。
```

这就是 `check` 约束。


---

## default约束

意义：保证事物的属性一定会有一个值。

我们还是写 学生表。我们先把上面新建的学生表先删除掉。

```sql
create table student
(
	stu_id int primary key,
	stu_sal int check (stu_sal>=1000 and stu_sal<=8000),
	stu_sex nchar(1) default ('男') --()可以省略。在数据库中字符串是必须用''括起来的
)
```

这里简单的解释一下：`''` 和 `""` 在数据库里面有什么区别？

**A：** `''` 就是表示一个字符串；`""` 就是表示一个数据的名字。（比如：为某一个事物去一个名字，用`""`。表的名字、约束的名字、列的名字、计算列的名字、临时表的名字。总之，只要是为一个事物取一个名字，就是：`""`。）



```sql
insert into student(stu_id, stu_sal) values (1, 1000)
insert into student values (2, 6000, '女')
```

选中这两行，点击 **执行** 按钮。

![Alt text](/images/2016-10-13-SQL-Learning-010-differences-tables-contraints-check-default-unique-not-null/1476254095140.png)

> `insert into student values (3, 2000)` 这样的命令是会报错的。因为表里面有3列值，你只输入了2列的数据。所以如果你想要让 `stu_sex ` 使用默认值，必须要要这样写：`insert into student(stu_id, stu_sal) values (1, 1000)`，指定你赋值的两列。


---

## unique（唯一）约束

意义：它保证了事物的属性的取值不允许重复，但是允许为空。

它都唯一了，那它和主键还有什么区别啊？

`unique（唯一）约束` 和 `允许为空` 是可以组合使用的。而 `主键` 和 `允许为空` 是不能组合使用的。

（**不允许为空**（`not null`）都可以和`unique（唯一）约束`、 `主键`  组合使用。）

 
 表里的项，如果不设置为 `not null` ，默认是：**允许为空** 的。

创建表：学生表2

```sql
create table student2
(
	stu_id int primary key,
	stu_sal int check (stu_sal>=1000 and stu_sal<=8000),
	stu_sex nchar(1) default ('男'), --()可以省略。在数据库中字符串是必须用''括起来的
	stu_name nvarchar(200) unique
)
```


我们执行下面的指令就会出错。因为 `stu_name ` 项是有唯一约束的：

```
insert into student2 vaules (1, 2000, '男', '张三')
insert into student2 vaules (2, 4000, '男', '张三')
```


我们执行下面的命令不会出错：（因为：`unique（唯一）约束` 和 `允许为空` 是可以组合使用的。）

```sql
insert into student2 values (3, 6000, '男', null)
```

如果我们执行下面的指令，就会出错：（因为，主键是不允许为空的。）

```sql
insert into student2 values (null, 6000, '女', '王麻子')
```


如果现在再插入一个为空的元组，就会出错：（错误时：重复）

（唯一约束不允许重复，但唯一约束允许为空，但是只允许其中有一列为空。）

```
insert into student2 values (4, 6000, '男', null)
```

---

**Q：** `unique（唯一）约束` 是否 允许多列为 `空`? 

**A：** 
在 **SQL Server** 软件只允许一个 `unique` 列为空；
`Oracle` 允许多个 `unique` 列为空。 

---

## 如何合理的利用主键和唯一约束建表

一个比较重要的问题：
**Q：** 唯一约束 和 主键 有什么区别？如何辨别？如何合理的利用主键和唯一约束建表？

**A：**


我们上网的时候，经常要登录，有些网站使用用户名，有的还可以使用邮箱登录。邮箱或者用户名，是唯一的。但不能使用它来当主键，我们不能使用业务信息当主键，因为用户名和邮箱是可以修改的。主键永远不可以修改。因为主键不但是本表的主键，而可能是其他表的外键，如果主键改变了，那么其他表的外键也要修改。所以，这个唯一键和主键的第一个区别。

第二区别，主键一遍最好使用数字，不要使用字符串。使用数字为主键，查新速度非常快，相比使用字符串。所以不能使用有实际意义的字符串当主键。再说一次：不要使用业务逻辑（虽然它也是不允许重复的，比如用户名和邮箱）当主键，要使用没有实际意义的编号当主键。（如果数据量太大，可能主键里面还需要加一下字母。）

主键最好不直接录入，我们最好使用 `identity` 关键字，让其自动增长，自动生成主键。（不使用业务逻辑当主键，使用代理主键（就是编号）当主键）

---


## 什么是`not null` 约束 以及 其 `not null` 约束与 `default` 约束的异同

我认为 `not null`  就是一个约束。它要求用户必须得为该属性赋一个值，否则语法出错！

如果一个字段不写`null` ，也不写 `not null` ，则默认是  `null` ，即默认允许为空，用户可以不给该字段赋值。

如果用户没有为该字段赋值，则该字段的值默认是 `null`。

要注意 `nul` 和 `default` 的区别。

* 相同点：都允许用户不赋值
* 不同点：`null` 修饰的字段如果用户不赋值则默认是`null`；`default` 修饰的字段如果用户不赋值则默认是`default` 指定的那个值。

---







