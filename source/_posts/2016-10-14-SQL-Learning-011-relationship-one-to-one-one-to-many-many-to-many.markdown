---
layout: post
title: "SQL 数据库 学习 011 关系、一对一、一对多、多对多"
date: 2016-10-14 21:18:48 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

## 什么是关系

定义：

* 表和表之间的联系。

实现方式：

* 通过设置不同形式的外键来体现表和表的不同关系。



## 关系的分类（假设是A表和B表）

## 第一种分类： 一对一  （详述一对一关系及其实现）

 （一对一，几乎不使用。所以，我们就一句话带过。） 

一对一的实现：既可以把表A的主键充当表B的外键，也可以把表B的主键充当表A的外键。


一对多 和 多对多 才是我们学习的重点。

## 第二种分类：一对多   （详述一对多关系及其实现）

一对多事怎么实现的？

表A（一）与表B（多）（我们现在希望，表A中的一条记录对应表B中的多条记录）之间要是有关系，就必须要有外键。把表A的主键添加到表B里面，充当表B的外键。

一对多的实现：在多的一方的表里面，添加外键。

## 第三种分类：多对多 （详述多对多关系及其实现）


现实中，什么事物和什么事物之间是多对多的关系？

班级和老师的关系。（一个班级有很多老师上课，一个老师可以去很多班级上课。）

多对多其实就是：一对多 和 多对一 的一个组合。

多对多的实现：多对多 必须要通过单独的一张表来表示。

* 班级是一张表
* 教师是一张表
* 班级和教师的关系也是一张表


用一个实例来解释 多对多。

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

解释代码：

其中`banji_id int constraint fk_banji_id foreign key references banji(bianji_id),` 代码中的 `fk_banji_id` 是约束的名字，`foreign key references banji(bianji_id)` 指的是：当前这个表里面的 `banji_id` 属性是来自 `banji ` 表的主键 `banji_id`，也就是说：当前表中的 `banji_id` 是一个外键（`foreign key `）。

其中`jiaoshi_id int foreign key references jiaoshi(jiaoshi_id),`里面，这里没有命名约束的名字，约束的名字可以省略不写，所以这里没有写也没有问题。同理上面那句代码。

其中`constraint pk_banji_id_jiaoshi_id primary key (banji_id, jiaoshi_id, kecheng)`中的 `pk_banji_id_jiaoshi_id ` 这个是约束的名字。`primary key (banji_id, jiaoshi_id, kecheng)` 是设置`jiaoshi_id` 和 `banji_id`  和 `kecheng` 三个属性的组合是一个**主键**（`primary key`）。


现在**执行**，生成了3个表。

现在我们在这3个表里面插入数据。

**banji**

![Alt text](/images/2016-10-14-SQL-Learning-011-relationship-one-to-one-one-to-many-many-to-many/1476450660605.png)


**jiaoshi**

![Alt text](/images/2016-10-14-SQL-Learning-011-relationship-one-to-one-one-to-many-many-to-many/1476450683275.png)


**banji_jiaoshi_mapping**

![Alt text](/images/2016-10-14-SQL-Learning-011-relationship-one-to-one-one-to-many-many-to-many/1476450197120.png)


都不会有错误，说明多对多生成成功。









