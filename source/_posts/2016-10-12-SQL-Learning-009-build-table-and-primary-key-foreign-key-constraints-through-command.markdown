---
layout: post
title: "SQL 数据库 学习 009 通过SQL命令 建表 和 主外键约束"
date: 2016-10-12 11:15:01 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

之前，我们介绍了[如何使用图形化操作建表和主外键约束](http://www.aobosir.com/blog/2016/10/11/SQL-Learning-008-build-tables-and-primary-foreign-key-constraints-with-GUI/)。这一节我们来介绍如何使用**命令**来**建表和主外键约束**。

---

## 使用命令 建表

**Step 0 . ** 先把之前在[这篇博客](http://www.aobosir.com/blog/2016/10/11/SQL-Learning-008-build-tables-and-primary-foreign-key-constraints-with-GUI/)里面建的表删除，我们先使用命令重新建。（如果你没有看这篇博客，就不需要做这一步的操作了。）

**Step 1 . ** 先选中（要建表的）库，然后点击 **新建查询**，输入下面的命令：（先建部门（`dept`）表，再建员工（`emp`）表）

```sql
create table dept
(
	dept_id int primary key,
	dept_name nvarchar(100) not null,
	dept_address nvarchar(100)
)

```

**Step 2 . ** 现在点击 对号 图标（分析），看看有没有语法错误。然后点击 **执行(X)** 按钮，来生成表。现在在做出的 **表** 里面右键 ，选择 **刷新** 。现在你就看到了，创建了一个新的表 `dept` 。

![Alt text](/images/2016-10-12-SQL-Learning-009-build-table-and-primary-key-foreign-key-constraints-through-command/1476239675315.png)

![Alt text](/images/2016-10-12-SQL-Learning-009-build-table-and-primary-key-foreign-key-constraints-through-command/1476239692934.png)


解释：`--`后面跟注释信息。**SQL** 定义变量和 **C++** 定义变量是反着的。



**Step 3 . ** 

```sql
create table emp
( --不能写成{} ，C++才写成}
	emp_id int constraint pk_emp_id_haha primary key,
	emp_name nvarchar(20) not null,
	emp_sex nchar(1),
	dept_id int constraint fk_dept_id_heihei foreign key references dept(dept_id)
)
```

解释：
1. 对于**约束**（`constraint`），要写一个名字（`pk_emp_id_haha ` 和 `fk_dept_id_heihei ` 都是自定义的名字），如果你不写名字，系统会自动给它分配一个名字。
2. `primary key` 是主键； `foreign key` 是外键。
3. `create table` 最后一个字段的后面建议不要写 `,` （逗号）。

选中这些命令。点击 `执行` 按钮。并刷新 **表**，`emp` 表就会出现。

![Alt text](/images/2016-10-12-SQL-Learning-009-build-table-and-primary-key-foreign-key-constraints-through-command/1476240682691.png)

![Alt text](/images/2016-10-12-SQL-Learning-009-build-table-and-primary-key-foreign-key-constraints-through-command/1476240702251.png)

`PK` 指的是 **主键** ；`FK` 指的是 `外键`。

![Alt text](/images/2016-10-12-SQL-Learning-009-build-table-and-primary-key-foreign-key-constraints-through-command/1476240725526.png)

下面的是我们刚刚定义的 `emp` 表的主键和外键的名字：

![Alt text](/images/2016-10-12-SQL-Learning-009-build-table-and-primary-key-foreign-key-constraints-through-command/1476240863958.png)

下面的是我们没有给取名字的 `dept` 表的主键的默认名字：

![Alt text](/images/2016-10-12-SQL-Learning-009-build-table-and-primary-key-foreign-key-constraints-through-command/1476240944813.png)

---

**总结：** 

使用命令 `create table` 来建表。


**Q：** 什么是约束？
**A：** **主键约束** 和 **外键约束** 的作用：

* 定义
	* 对一个表中的属性操作的限制叫做约束。
* 分类
	* 主键约束
		* 不允许重复元素 避免了数据的冗余。
	* 外键约束
		* 通过外键约束从语法上保证了本事物所关联的其他事物一定是存在的。（就是说：事物与事物之前的关系是通过外键来体现的）

你要是感觉命令很难，就多敲，敲一敲就好了。

---