---
layout: post
title: "SQL 数据库 学习 027 查询-10 group by ---  以某字段分组"
date: 2016-10-17 13:05:12 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, group by, 分组]
---





---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## `group by` --- 以某字段分组

```sql
--输出每个部门的编号 和 该部门的平均工资
select deptno, avg(sal) as "部门平均工资"
	from emp
	group by deptno
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680047590.png)

---

```sql
-- 判断下面语句是否正确
select deptno, avg(sal) as "部门平均工资" ename
	from emp
	group by deptno
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680188160.png)


总结： 使用了 `group by` 之后， `select` 中只能出现分组后的整体信息，不能出现组内的详细信息。

```sql
--error
select *
	from emp
	group by deptno, job
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680255640.png)


```sql
--error
select deptno, job, sal
	from emp
	group by deptno, job
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680302040.png)


```sql
select deptno, job, avg(sal)
	from emp
	group by deptno, job
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680344010.png)


显示的不是很好，我们就对其进行排序。（没有实际的意义，我们就是讲讲语法。）

```sql
select deptno, job, avg(sal)
	from emp
	group by deptno, job
	order by deptno
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680377389.png)


只要是聚合函数，在这里都可以使用。

```sql
select deptno, job, avg(sal), count(*), sum(sal),  min(sal)
	from emp
	group by deptno, job
	order by deptno
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680445168.png)

---

```sql
select deptno, job, avg(sal) "平均工资", count(*) "部门人数", sum(sal) "部门总工资",  min(sal) "部门最低工资"
	from emp
	group by deptno, job
	order by deptno
```

![Alt text](/images/2016-10-17-SQL-Learning-027-Query-10-group-by/1476680508397.png)


---

**总结：**

 `group by` 

* 格式： `group by 字段的集合`
* 功能：把表中的记录按照字段分成不同的组
* 注意：理解 `group by a, b, c` 的用法
	* 先按 `a` 分组，如果 `a` 相同，再按 `b` 分组，如果 `b` 相同，再按 `c` 分组。最终统计的最小分组的信息。

---


