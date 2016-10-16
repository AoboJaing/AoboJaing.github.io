---
layout: post
title: "SQL 数据库 学习 021 查询-04 in 的用法 --- 属于若干个孤立的值"
date: 2016-10-17 00:39:00 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, in]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---


```sql
select * from emp where sal in (1500, 3000)
```

![Alt text](/images/2016-10-17-SQL-Learning-021-Query-04-in-the-usage/1476635565178.png)


---

```sql
select * from emp where sal in (1500, 3000, 5000)
	--把sal里面是1500 和 3000 和 5000 的值都输出
```

![Alt text](/images/2016-10-17-SQL-Learning-021-Query-04-in-the-usage/1476635600379.png)

上面的命令等价于：

```sql
select * from emp
	where sal=1500 or sal=3000 or sal=5000
```

---

---

```sql
select * from emp where sal not in (1500, 3000, 5000)
```

![Alt text](/images/2016-10-17-SQL-Learning-021-Query-04-in-the-usage/1476635684012.png)

上面的命令等价于：

```sql
select * from emp
	where sal<>1500 and sal<>3000 and sal<>5000
		--在数据库中 不等号有两种表示： != 和 <> ，推荐使用第二种
		--对或（or）取反是并且（and） 对并且（and）取反是或（or）
```




---





















