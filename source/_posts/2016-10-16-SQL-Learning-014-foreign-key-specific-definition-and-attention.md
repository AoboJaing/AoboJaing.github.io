---
layout: post
title: "SQL 数据库 学习 014 外键的具体定义 设计外键要注意的问题"
date: 2016-10-16 17:12:56 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

## 外键的具体定义

如果一个表中的若干个字段是来自另外若干个表的主键或唯一键，则这若干个字段就是外键。（我们讲[多对多](http://www.aobosir.com/blog/2016/10/14/SQL-Learning-011-relationship-one-to-one-one-to-many-many-to-many/)的时候，一个表里面就有两个外键。）


## 设计外键要注意的问题

* 外键通常是来自另外表的主键而不是唯一（`unique`）键，因为唯一键可能为`null`。
* 外键不一定是来自另外的表，也可能来自本表的主键
* 含有外键的表叫外键表，外键字段来自的那一张表叫做主键表


---

## 问题：

**Q：** 先删除主键表还是先删除外键表？

**A：** 先删除外键表，再删主键表。如果先删除主键表，会报错，因为这会导致外键表中的数据引用失效。

	
