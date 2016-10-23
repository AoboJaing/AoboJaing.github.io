---
layout: post
title: "SQL 数据库 学习 032 identity的用法 --- 如何设置主键自动增长（用户不需要为identity修饰的主键赋值）"
date: 2016-10-24 05:28:22 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, identity, 主键]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## `identity` 的用法 --- 如何设置主键自动增长（用户不需要为identity修饰的主键赋值）


```sql
create table student3
(
	student_id int primary key identity (100, 5),
	student_name nvarchar(200) not null
)

select * from student3
insert into student3 (student_name) values ('张三');
insert into student3 values ('李四');  -- ok
delete from student3 where student_name = '李四';
insert into student3 (student_name) values ('王五');
```



## 如何重新设置`identity` 字段的值

表中删除数据又插入数据会导致主键不连续递增 怎么办？

不重要。主键是否连续增长不是非常重要。


如果对表中数据进行了删除操作，如何让 `identity` 字段重新从某个值开始自增？

```sql
create table emp
(
	empid int identity(1, 1),
	ename nvarchar(20) not null
);

insert into emp values('aaaa');
insert into emp values('bbbb');
insert into emp values('cccc');
insert into emp values('dddd'); -- 10行
select * from emp
delete from emp where emp where wmpid=4 -- 删除empid为4的记录
select * from emp
insert into emp values('eeee') -- 因为执行10行时empid为4，所以执行本句时，empid为5
select * from emp
delete from emp where empid=5
dbcc checkident('emp', reseed, 3) -- 17行 把emp表中identity字段的初始值重新设置为3

insert into emp values('eeee') -- 此时插入记录时。empid为4，因为17行代码把empid设置成了3
select * from emp
```

```sql
dbcc checkident('emp', reseed, 0)
```

种子的值也可以是零，这样设置的话，用户插入值时，种子的初始值将从1开始。

---

**总结：**

`identity` 表示该字段的值会自动更新，不需要我们维护，通常情况下我们不可以直接给 `identity` 修饰的字符赋值，否则编译时会报错。

语法格式为：

* `identity [(m, n)]`
* `m` 表示的是初始值，`n` 表示的是每次自动增加的值
* 要么同时指定 `m` 和 `n` 的值，要么 `m` 和 `n` 都不指定，不能只写其中一个值。如：`identity(3,2)`、`identity`  都是正确的，但是 `identity(3)`、`identity(2)`、`identity` 都是错误的。
* 如果 `m` 和 `n` 都未指定，则取默认值`(1, 1)`

数据类型是整型的列才能被定义成标识列：

* `int`、`bigint`、`smallint` 列都可以被定义成 `identity`
* 不含有小数位的 `decimal` 和 `numeric` 也可以被标记为 `identity`。如：`decimal`、`decimal(6, 0)` 字段都可以被标记为 `identity`，但是 `decimal(6, 2)` 字段就不能被标记为  `identity`

标识列通常与 `primary key` 约束一起用作表的唯一行标识符：

* 非主键也是可以被定义为 `identity`的，但不推荐。


---

## 如何向 `identity` 字段插入数据

通常`identity`标记的字段我们是不需要插入数据的，即我们不需要维护 `identity` 字段的值，它会自动更新，如果我们需要向`identity`修饰的字段插入值，则必须满足如下两点：

1. 先得执行 `set identity_insert [database.[owner.]] {table} {on | off}`
2. 插入数据时必须得指定 `identity` 修饰的字段的名字

---

## 如何向 `identity` 字段插入数据示例

```sql
create database Test
use test;
create table dept
(
	deptid decimal(6, 0) identity,
	deptname varchar(20),
);
set identity_insert test.dbo.dept on
	--执行本语句的目的是：希望可以向identity修饰的字段插入值
	--不可以改为set identity_insert dept on
	--不可以改为set identity_insert dbo.test.dept on
	--不可以改为set identity_insert dbo.test.dept.on
insert into dept (deptid, deptname) values (1, 'zhangsan')
	--不能改为：insert into dept values (1, 'zhangsan') -- 13
```

默认情况下，使用`identity`关键字修饰的主键是自动增长的，如果想手动设置主键的值，需要先将目标表打开：`set identity_insert test.dbo.dept on`，然后再使用`insert into dept (deptid, deptname) values (1, 'zhangsan')` 命令来手动设置主键的值。

---








