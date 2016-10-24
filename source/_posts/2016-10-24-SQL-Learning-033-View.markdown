---
layout: post
title: "SQL 数据库 学习 033 视图"
date: 2016-10-24 09:13:55 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 视图]
---




---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## 为什么需要视图

以一个例子为例： 

**求出平均工资最高的部门的编号和部门的平均工资。**

```sql
--使用我们目前所知道的方法去编写查询代码。
select *
	from (
		select deptno, avg(sal) "avg_sal"
			from emp
			group by deptno
	) "T"
	where "T"."avg_sal" = (
		select max("E"."avg_sal") from (
			select deptno, avg(sal) "avg_sal"
				from emp
				group by deptno
		) "E"
	)
```

上面的查询代码中，有下面的一段代码，这段代码是创建一个临时表。我们可以将这个临时表创建为一个视图：

```sql
		select deptno, avg(sal) "avg_sal"
			from emp
			group by deptno
```

创建了一个视图：

```sql
create view v$_emp_1
as
	select deptno, avg(sal) "avg_sal"
		from emp
		group by deptno
```

输出这个视图中的数据信息：

```sql
select * from v$_emp_1
```

下面的代码的输出同上面**使用目前所知道的方法去编写查询代码**。

```sql
select * from v$_emp_1
	where avg_sal = (select max(avg_sal) from v$_emp_1)
```

**总结：** 视图的优点是可以简化查询代码。（简化查询）。即避免了代码的冗余；避免了属性大量重复的**sql**语法。

---

## 什么是视图

* 视图从代码上看视图是一个`select`语句。
* 视图从逻辑上被当做一个虚拟表看待。

---

## 如何创建视图

视图的格式

```sql
create view 视图的名字
	as
		--select的前面不能添加begin
		select
		--select的后面不能添加end
```


---

## 视图的优点

1. 视图的优点是可以简化查询代码。
2. 增加数据的保密性

```sql
--屏蔽了入职日期和员工工资 这两个属性。
create view v$_emp2
as
	select empno, ename, job, mgr, comm, deptno 
		from emp
```

---

## 视图的缺点

1. 增加了数据库维护的成本。
	* 原表里面的属性被改了，那么视图就会报错。
2. 视图只是简化了查询的代码，但是并不能加快查询的速度，这也是视图使用不足的地方。

---

## 使用视图要注意的三个问题

1 . 创建视图的`select`语句必须得为所有的计算列指定别名

```sql
--error
create view v$_a
as
	select avg(sal) from emp;
```
```sql
--ok
create view v$_a
as
	select avg(sal) as "avg_sal" from emp;
```

2 . 视图不是物理表，而是虚拟表

3 . 不建议通过视图更新视图所依赖的原始表的数据和结果。（因为很麻烦，有许多语法的限制。）


---