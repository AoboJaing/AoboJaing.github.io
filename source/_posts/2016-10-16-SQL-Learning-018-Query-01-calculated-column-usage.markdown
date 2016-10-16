---
layout: post
title: "SQL 数据库 学习 018 查询-01 计算列 的用法"
date: 2016-10-16 20:15:30 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, 计算列]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## 计算列


```sql
select * from emp;
	-- * 表示所有的
	-- * from emp 表示从emp表查询
```

执行输出：

![Alt text](/images/2016-10-16-SQL-Learning-018-Query-01-calculated-column-usage/1476619600875.png)

---

```sql
select empno, ename from emp;
	-- 将员工表里面所有员工的 empno 和 ename 都输出出来
```

执行输出：

![Alt text](/images/2016-10-16-SQL-Learning-018-Query-01-calculated-column-usage/1476619649220.png)

---

```sql
select ename, sal*12 as "年薪" from emp;
	-- as 可以省略。 记住："年薪" 不要写成 '年薪' 、也不要写成 年薪
```

执行输出：

![Alt text](/images/2016-10-16-SQL-Learning-018-Query-01-calculated-column-usage/1476619727923.png)


**注意：** ： 在**Oracle**软件中字段的别名不允许用单引号括起来。但是 **SQL Server** 软件却允许，因此为了兼容性考虑，最好字段的别名用`""`（双引号）括起来，不要使用`''`（单引号）。

上面这段命令 `select ename, sal*12 as "年薪" from emp` 就是计算列。解释：原本 `emp` 表里面没有 年薪 这个属性，我们使用 ` sal*12 as "年薪"` 得到年薪的信息，这就是 **计算列**。

---

```sql
select 5 from emp;
	-- ok，可以运行
	--输出的行数是emp表的行数，每行只有一个字段，值是5
	-- 5 就是一个值，仅此而已，没有实际意义
```

执行输出：

![Alt text](/images/2016-10-16-SQL-Learning-018-Query-01-calculated-column-usage/1476619771628.png)

---

```sql
select 5;
	--ok，可以运行
	--但是不推荐
```

执行输出：

![Alt text](/images/2016-10-16-SQL-Learning-018-Query-01-calculated-column-usage/1476619797016.png)

---

```sql
select ename, sal*12 as "年薪", sal "月薪", job from emp;
```

执行输出：

![Alt text](/images/2016-10-16-SQL-Learning-018-Query-01-calculated-column-usage/1476619867716.png)

---




















