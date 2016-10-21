---
layout: post
title: "SQL 数据库 学习 030 查询-13 --- 查询语句的顺序"
date: 2016-10-21 20:54:28 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, 查询语句顺序]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---


## **SQL Server** 查询语句的顺序

```sql
select top ...
	from A
	join B
	on ...
	join C
	on ...
	where ...
	group by ...
	having ...
	order by ...
```

---

## 例子

> 本例子里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

**求出平均薪水最好的部门的标号和部门的平均工资**

```sql
--求出平均薪水最好的部门的标号和部门的平均工资
--第1种写法：
select top 1 deptno, avg(sal) "avg_sal"
	from emp "E"
	group by deptno
	order by avg(sal) desc
```

![Alt text](/images/2016-10-21-SQL-Learning-030-Query-13-Query-order-of-order/1477040016720.png)

等价于：

```sql
--求出平均薪水最好的部门的标号和部门的平均工资
--第2种写法：
select "E".*
	from (
		select deptno, avg(sal) "avg_sal"
			from emp
			group by deptno
	) "E"
	where "E"."avg_sal" = (
		select max("avg_sal") 
			from (
				select deptno, avg(sal) "avg_sal" 
					from emp 
					group by deptno
			) "T"
	)
```

![Alt text](/images/2016-10-21-SQL-Learning-030-Query-13-Query-order-of-order/1477044470627.png)


---





