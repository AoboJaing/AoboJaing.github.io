---
layout: post
title: "SQL 数据库 学习 031 查询-14 连接查询 ---  左（右）外连接、完全连接、交叉连接、联合"
date: 2016-10-22 18:17:33 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, left join, right join, full join, cross join, innor join, union]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

# 连接查询

**定义：** 

将两个表或者两个以上的表以一定的连接条件连接起来。从中检索出满足条件的数据。

---


## 内连接 （`innor join` 或者 `join`）

请看这篇博客：[SQL 数据库学习 查询 --- 内连接](http://www.aobosir.com/blog/2016/10/21/SQL-Learning-029-Query-12-Connection-query-the-connection/)。

---

## 左（右）外连接 （`left join` 和 `right join`）

```sql
select * from emp "E"
	left join dept "D"
	on "E".deptno = "D".deptno
```

![Alt text](/images/2016-10-22-SQL-Learning-31-Query-14-Join-Query-Left-Right-Join-Full-Join-Cross-Join-Union/1477131219555.png)

实现的步骤：

1. 用左表的第一行分别和右表的所有行进行的连接，如果有匹配的行，则一起输出，如果右表有多行匹配，则结果集输出多行，如果没有匹配行，则结果集中只输出一行，该输出行左边为左表第一行内容，右边全部输出`null`。
2. 然后再用左表第二行和右边所有行进行连接，如果没有匹配行，则结果集中只输出一行，该输出行左边为左表第二行内容，右边全部输出`null`。
3. 以此类推，直至左边所有行连接完毕。
4. 因为右边很可能出现有多行和左边的某一行匹配，所以左连接产生的结果集的行数很可能大于 `left join` 左边表的记录的总数。
5. 帮助文档：左向外连接的结果集包括`LEFT OUTER` 子句中指定的左表的所有行，而不仅仅是连接列所匹配的行。如果左表的某行在右表中没有匹配行，则在相关联的结果集行中右表的所有选择列表均为空值。

---

左外连接的实际意义

* 返回一个事情及其该事物的相关信息，如果该事物没有相关信息，则输出`null`
* 例子：
	* 已知条件： `productStocks` 货物库存表、 `orderform` 订单表、`pID` 是产品的编号
	* **sql语句**
	* `select productStocks.*, orderform.* from productStocks left join orderform on productStocks.pID=orderform.pID`
	* 实际意义： 返回仓库中现存货物的信息及其该货物的订单信息，如果该货物没有订单信息，在把该货物的订单信息全部输出为`null`。

---

## 完全连接（`full join`）

```sql
select * from productStocks
	full join orderform
	on productStocks.pid = orderform.pid
```

![Alt text](/images/2016-10-22-SQL-Learning-31-Query-14-Join-Query-Left-Right-Join-Full-Join-Cross-Join-Union/1477131238849.png)


结果集中包含三部分内容：

1. 两个表中匹配的所有行记录
2. 左表中那些在右表中找不到匹配的行的记录。这些记录的右边全为`null`
3. 右表中那些在左表中找不到匹配的行的记录。这些记录的左边全为`null`

---

## 交叉连接（`cross join`）

```sql
select *
	from emp
	cross join dept
```

等价于：

```sql
select * from emp, dept
```

效果都是将两个表进行笛卡尔积。

![Alt text](/images/2016-10-22-SQL-Learning-31-Query-14-Join-Query-Left-Right-Join-Full-Join-Cross-Join-Union/1477131282846.png)

---

## 自连接

**定义：** 一张表自己和自己连接起来查询数据。

例子：不准用聚合函数 求薪水最高的员工的信息。

```sql
--用聚合函数 求出薪水最高的员工的信息
select * 
	from emp
	where sal = (select max(sal) from emp)
```


```sql
--不准用聚合函数 求出薪水最高的员工的信息
select * from emp 
	where empno not in (
		select distinct "E1".empno
		from emp "E1"
		join emp "E2"
		on "E1".sal < "E2".sal
	)
```

![Alt text](/images/2016-10-22-SQL-Learning-31-Query-14-Join-Query-Left-Right-Join-Full-Join-Cross-Join-Union/1477063139982.png)

---

## 联合（`union`）

**例子：** 

输出每一个员工的姓名、工资、上司的姓名。

```sql
select "E1".ename as "员工姓名","E1".sal as "员工工资", "E2".ename as "上司姓名" 
	from emp "E1", emp "E2"
	where "E1".mgr = "E2".EMPNO 
union
select ename, sal, '已是最大老板' from emp where mgr is null
```

![Alt text](/images/2016-10-22-SQL-Learning-31-Query-14-Join-Query-Left-Right-Join-Full-Join-Cross-Join-Union/1477130066693.png)

---

**定义：**

表和表之间的数据以纵向的方式连接在一起。注意：我们以前讲的所有的连接是以横向的方式连接在一起的。

**注意：**

联合就是：若干个`select` 子句要联合成功的话，必须得满足两个条件：

1. 这若干个 `select` 子句输出的列数必须是相等的。
2. 这若干个 `select` 子句输出列的数据类型至少是兼容的。


---



