---
layout: post
title: "SQL 数据库 学习 012 数据库关系图"
date: 2016-10-16 15:47:58 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

我们现在写一个 多对多关系的表：（这段代码你可以在[这篇博文](http://www.aobosir.com/blog/2016/10/14/SQL-Learning-011-relationship-one-to-one-one-to-many-many-to-many/)里面看到它的代码解释。）


```sql
--班级表
create table banji
(
	banji_id int primary key,
	banji_num int not null,
	banji_name nvarchar(100)
)

--教师
create table jiaoshi
(
	jiaoshi_id int primary key,
	jiaoshi_name nvarchar(200)
)

--第三张表：用来模拟班级和教师的关系
create table banji_jiaoshi_mapping
(
	banji_id int constraint fk_banji_id foreign key references banji(bianji_id),
	jiaoshi_id int foreign key references jiaoshi(jiaoshi_id),
	kecheng nvarchar(20),
	constraint pk_banji_id_jiaoshi_id primary key (banji_id, jiaoshi_id, kecheng)
	
)

```



虽然，现在我们已经将表与表之间的关系都建好了。但是我现在怎么才能知道他们之间的关系到底有没有见好啊。
**SQL Server** 为我们提供了另外一个工具：**数据库关系图**。

我们新建一个：

![Alt text](/images/2016-10-16-SQL-Learning-012-database-diagram/1476602645224.png)

![Alt text](/images/2016-10-16-SQL-Learning-012-database-diagram/1476602656133.png)

外键添加到多的一方。

---

