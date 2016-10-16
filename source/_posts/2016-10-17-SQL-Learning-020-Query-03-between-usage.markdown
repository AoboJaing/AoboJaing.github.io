---
layout: post
title: "SQL 数据库 学习 020 查询-03 between 的用法"
date: 2016-10-17 00:20:53 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, between]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## `between` 的用法

```sql
--查找工资在1500到3000之间（包括1500和3000）的所有的员工的信息
select * from emp
	where sal>=1500 and sal<=300
```

![Alt text](/images/2016-10-17-SQL-Learning-020-Query-03-between-usage/1476634590985.png)


---

上面的指令等价于：

```sql
select * from emp
	where sal between 1500 and 3000
```

---

```sql
--查找工资在小于1500或大于3000之间的所有的员工的信息
select * from emp
	where sal<1500 or sal>3000
```

![Alt text](/images/2016-10-17-SQL-Learning-020-Query-03-between-usage/1476634665094.png)


---

上面的指令等价于：

```sql
select * from emp
	where sal not between 1500 and 3000
```

---



