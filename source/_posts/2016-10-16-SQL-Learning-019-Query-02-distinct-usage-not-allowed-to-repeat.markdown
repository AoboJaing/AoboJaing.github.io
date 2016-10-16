---
layout: post
title: "SQL 数据库 学习 019 查询-02 distinct 的用法 --- 不允许重复"
date: 2016-10-16 21:10:52 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, distinct]
---



---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## `distinct` 的用法

`distinct` 的意思是：不允许重复。 

```sql
select deptno from emp;
	-- 14行记录 不是3行记录
```

![Alt text](/images/2016-10-16-SQL-Learning-019-Query-02-distinct-usage-not-allowed-to-repeat/1476623018150.png)

---

```sql
select 10000 from emp;
	-- 也是14行记录
```

![Alt text](/images/2016-10-16-SQL-Learning-019-Query-02-distinct-usage-not-allowed-to-repeat/1476623063142.png)

---

```sql
select distinct deptno from emp;
	--distince deptno 会过滤掉重复的deptno
```

![Alt text](/images/2016-10-16-SQL-Learning-019-Query-02-distinct-usage-not-allowed-to-repeat/1476623127746.png)


---

```sql
select distinct comm from emp;
	--distince 也可以过滤掉重复的null。或者说如果有多个null，只输出一个
```

![Alt text](/images/2016-10-16-SQL-Learning-019-Query-02-distinct-usage-not-allowed-to-repeat/1476623177137.png)


---

```sql
select distinct comm, deptno from emp;
	--把 comm 和 deptno 的组合进行过滤
```

![Alt text](/images/2016-10-16-SQL-Learning-019-Query-02-distinct-usage-not-allowed-to-repeat/1476623219322.png)


---

```sql
select deptno, distinct comm from emp;
	--error 逻辑上有冲突
```

执行输出错误：

```
消息 156，级别 15，状态 1，第 11 行
关键字 'distinct' 附近有语法错误。
```

---


