---
layout: post
title: "SQL 数据库 学习 026 查询-09 聚合函数 ---  怎样编写模糊查询语句"
date: 2016-10-17 11:05:58 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, 聚合函数, 模糊查询]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---


## 函数的分类


单行函数

* 每一行返回一个值

---

多行函数

* 多行返回一个值
* 聚合函数是多行函数

---

例子：

```sql
select lower(ename) from emp;
	--最终返回的是14行
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476672968757.png)

---

```sql
select max(sal) from emp;
	--返回时1行 max() 是多行函数
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476672998766.png)


---

## 聚合函数的分类

* `max()` 求最大值
* `min()` 求最小值
* `avg()` 平均值
* `count()` 求个数
	* `count(*)` ：返回表中所有的记录的个数
	* `count(字段名)` : 返回字段值非空的记录的个数， 重复的记录也会被当做有效记录
	* `count(distinct 字段名)` ：返回字段不重复并且非空的记录的个数

```sql
select count(*) from emp;
	--返回emp表所有记录的个数
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476673037243.png)


---

```sql
select count(deptno) from emp;
	--返回值是14，这说明deptno重复的记录也被当做有效的记录
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476673083683.png)

---


```sql
select count(distinct deptno) from emp;
	--返回值是3， 统计deptno不重复的记录的个数
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476673123560.png)


---

```sql
select count(comm) from emp;
	--返回值是4。 这说明comm为null的记录不会被当做有效的记录
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476673148684.png)

---

## 注意的问题

```sql
select max(sal), min(sal), count(*) from emp;
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476673188904.png)

---

```sql
select max(sal) "最高工资", min(sal) "最低工资", count(*) "员工人数" from emp;
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476673238975.png)

---

```sql
select max(sal), lower(ename) from emp;
	--error 单行函数和多行函数不能混用
```

![Alt text](/images/2016-10-17-SQL-Learning-026-Query-09-aggregate-function-fuzzy-query/1476673278431.png)


---






















