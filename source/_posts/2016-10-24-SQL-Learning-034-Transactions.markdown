---
layout: post
title: "SQL 数据库 学习 034 事务"
date: 2016-10-24 13:20:24 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 事务, transaction]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---


## 为什么需要事务

事务主要用来保证数据的合理性和并发处理的能力！

通俗的说：

* 事务可以保证避免数据处于一种不合理的中间状态
* 利用事务可以实现多个用户对共享资源的同时访问

例子：

银行中的转账操作，账户A把一定数量的款项转到账户B上，这个操作包括两个步骤，一个是从账户A上把存款减去一定数量，二是在账户B上把存款加上相同的数量。这两个步骤显然要么都完成，要么都取消，否则银行就会受损失。显然，这个转账操作中的两个步骤就构成一个事务。

假设A和B用户都希望查询修改M表数据，A用户不应该刚把M表的数据改成5，查询时显示的数据却是8（因为B用户修改M表的数据成8了）。事务必须得保证多个用户对共享资源同时访问时，数据库给用户的反应是合理的。

事务就是专门解决这个问题的。

---

## 什么是事务

一系列操作要么全部执行成功，要么全部执行失败，这就是事务。

---

## 如何创建事务

**T-SQL** 使用下列语句管理事务：

* 开启事务：`begin transaction`
* 提交事务：`commit transaction`
* 回滚（撤销）事务：`rollback transaction`

一旦事务提交或回滚，则事务结束。

判断某条语句执行是否出错：

* 使用全局变量 `@@error`
* `@@error` 只能判断当前一条**T-SQL**语句执行是否有错，为了判断事务中所有**T-SQL**语句是否有错，我们需要对错误进行累计。如：`set @errorSum=@errorSum+@@error`



---

## 初学者必须要掌握的三个问题：

一 . 事务时用来研究什么的：

* 避免数据处于不合理的中间状态。（比如：转账）
* 怎样避免多用户同时访问时，呈现给用户的数据是合理的。

二 . 事务和线程的关系：

事务也是通过锁来解决很多问题的。（线程同步就是通过锁来解决的 `sychronized`）

三 . 事务和第三方插件的关系：

* 直接使用事务库技术难度很大，很多人是借助第三方插件来实现。（因为我们一般人不需要细细的研究数据库中事务的语法细节。）
* 第三方插件要想完成预期的功能，一般必须得借助数据库中的事务机制。

---

## 事务 --- 总结 和 实例


总结事务的四大特性：事务必须具备以下四个属性，简称**ACID**属性。

* 原子性：事务是一个完整的操作。事务的各步操作是不可分的（原子的）；要么都执行，要么都不执行。
* 一致性：当事务完成时，数据必须处于一致状态，要么处于开始状态要么处于结束状态，不允许出现中间状态！
* 隔离性：指当前的事务与其他未完成的事务是隔离的。在不同的隔离级别下，事务的读取操作，可以得到的结果是不同的。
* 持久性：事务完成后，它对数据库的修改被永久保持，事务日志能够保持事务的永久性。


**一个例子：**

```sql
--创建Test库
create database Test
--进入Test库
use Test
--创建一个bank表
create table bank
(
	customerEname nvarchar(200),
	currrentMoney money
)
--插入数据
insert into bank values ('张三', 1000)
insert into bank values ('李四', 1)
--给bank表中的currentMoney属性添加一个约束
alter table bank add constraint check_currentMoney check(currentMoney>=1)
```

现在我要将张三的1000打给李四。（这样做会失败，因为上面已经给`check_currentMoney`属性添加了一个约束：`currentMoney>=1`）。

普通的查询指令进行转账：

```sql
update bank set currentMoney=currentMoney-1000 where customerEname='张三'
update bank set currentMoney=currentMoney+1000 where customerEname='李四'
```

使用事务实现进行转账：（不重要，掌握就可以，语法怪异，实用性不强。）

```sql
begin transaction
declare @errorSum int
set @errorSum = 0
update bank set currentMoney=currentMoney-1000
	where customerEname='张三'
set @errorSum = @errorSum + @@error
update bank bank set currentMoney=currentMoney+1000
	where customerEname='李四'
set @errorSum = @errorSum + @@error
if (@errorSum <> 0)
	begin
		print '转账失败'
		rollback transaction
	end
else
	begin
		print '转账成功'
		commit transaction
	end
```















