---
layout: post
title: "SQL 数据库 学习 022 查询-05 top 的用法 --- 最前面的若干个记录"
date: 2016-10-17 00:55:57 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, top]
---




---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## `top` ---  输出最前面的若干个记录


```sql
select top 5 * from emp;
	--输出从emp表的上面数，前5个元组
```

![Alt text](/images/2016-10-17-SQL-Learning-022-Query-05-top-usage/1476636796825.png)

---

```sql
select top 15 percent * from emp;
	--输出从emp表的上面数，15%的元组。（输出的是3个，不是2个）
```

![Alt text](/images/2016-10-17-SQL-Learning-022-Query-05-top-usage/1476636830654.png)

---




