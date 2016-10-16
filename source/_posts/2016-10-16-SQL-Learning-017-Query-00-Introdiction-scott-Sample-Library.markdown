---
layout: post
title: "SQL 数据库 学习 017 查询-00 介绍 scott 例子库"
date: 2016-10-16 19:40:10 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

我们要查数据，总先得有数据要查吧，所以我们需要先找一个例子库。**Orale**软件里面就有一个例子库，这个库很经典，就是：`scott` 库。

## 附加 `scott` 库

如何添加一个 `scott` 数据库 到服务器中，请参考[这个网站](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)。


---

## 介绍 `scott` 库

要想查询一个表，第一件事情就必须十分了解一个库里面所有的表 和 表与表之间的关系。

这个 `scott` 库里面一共有三个表：

![Alt text](/images/2016-10-16-SQL-Learning-017-Query-00-Introdiction-scott-Sample-Library/1476616454316.png)


---

先看看 `emp` 表（**员工表**）

![Alt text](/images/2016-10-16-SQL-Learning-017-Query-00-Introdiction-scott-Sample-Library/1476616536461.png)

员工表里面有8个属性：

`EMPNO`（员工编号）、`ename`（姓名）、`job`（职称）、`mgr`（上级编号）、`hiredate`（雇佣日期）、`sal`（工资）、`comm`（奖金）、`deptno`（部门编号）。

里面 `job` 属性里面的英文单词翻译：

* **CLERK** ：普通职员
* **SALESMAN** ：销售人员
* **MANAGER** ：经理
* **ANALYST** ：研究人员
* **PRESIDENT** ：总统


---

现在我们看看 `dept` 表 （**部门表**）：

![Alt text](/images/2016-10-16-SQL-Learning-017-Query-00-Introdiction-scott-Sample-Library/1476617073131.png)

部门表里面有3个属性：`deptno`（部门编号）、`dname`（部门名称）、`loc`（地址）。

---

在看看最后一个表：`SALGRAGE` 表。（这个**表**表示的是**工资的等级**表。）


![Alt text](/images/2016-10-16-SQL-Learning-017-Query-00-Introdiction-scott-Sample-Library/1476617149867.png)

`SALGRADE` 表里面有3个属性：`GRADE`（等级）、`LOSAL`（下限）、`HISAL`（上限）。

---


