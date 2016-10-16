---
layout: post
title: "SQL 数据库 学习 023 查询-06 null 的用法 --- 没有值 空值"
date: 2016-10-17 01:48:03 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, null]
---




---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---


## `null` --- 没有值、空值


```sql
--null不能参与<> != = 运算
select * from emp where comm <> null; --输出为空 error
select * from emo where comm != null; --输出为空 error
select * from emp where comm = null; --输出为空 error
```

```sql
--null 可以参与is 、 not is 
select * from emp where comm is null; 
	--输出奖金为空的员工的信息
select * from emp where comm is not null;
	--输出奖金不为空的员工的信息
```


```sql
--任何类型的数据都允许为null
create table t1 (name nvachar(20), cnt int, riqi datetime)
insert into t1 values (null, null, null)
select * from t1;
```


```sql
--输出每一个员工的姓名、年薪（包含了奖金）、comm假设是一年的奖金
select ename, sal*12+comm "年薪" from emp;
	--这段指令证明了：null不能参与任何数学运算，结果永远是null
```


```sql
--正确的写法
select ename, sal*12+isnull(comm, 0) from emp;
	--isnull(comm, 0) 如果comm是null，就返回为0，否则返回comm的值。
```


---

**总结：**

* `0` 和 `null` 是不一样的，`null` 表示空值，没有值，`0`表示一个确定的值
* `null` 不能参与如下运算：`<>`、`!=`、`=`
* `null` 可以参与如下运算：`is`、`not is`
* 任何类型的数据都允许为`null`
* null不能参与任何数学运算，结果永远是null








