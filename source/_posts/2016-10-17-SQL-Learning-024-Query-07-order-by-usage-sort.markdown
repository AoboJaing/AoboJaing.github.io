---
layout: post
title: "SQL 数据库 学习 024 查询-07 order by 的用法 --- 以某个字段排序"
date: 2016-10-17 03:13:40 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, order by]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---

## `order by` --- 以某个字段排序

**例子：**

```sql
select * from emp order by sal;
	--默认是按照升序排序
```

![Alt text](/images/2016-10-17-SQL-Learning-024-Query-07-order-by-usage-sort/1476644715874.png)

---

```sql
select * from emp order by deptno, sal;
	--先按照deptno排序，然后再按照sal排序
```

![Alt text](/images/2016-10-17-SQL-Learning-024-Query-07-order-by-usage-sort/1476644847648.png)

---

```sql
--asc是升序的意思，默认可以不写 desc是降序
select * from emp order by deptno desc, sal;
	--先按照deptno降序排序，如果deptno相同，再按照sal升序排序
	--记住sal是升序不是降序
	--order by a desc, b, c, d   desc只对a产生影响，不会对后面的b, c, d 产生影响
```

![Alt text](/images/2016-10-17-SQL-Learning-024-Query-07-order-by-usage-sort/1476644919129.png)

---


```sql
select * from emp order by deptno, sal desc
	--问题：desc是否会对deptno产生影响？
	--答案：不会
	--先按deptno升序，如果deptno相同，再按sal降序排序
```

![Alt text](/images/2016-10-17-SQL-Learning-024-Query-07-order-by-usage-sort/1476644983662.png)


---

**总结：**

* `order by a, b				--a和b都是升序`   
* `order by a, b desc			--a升序 b降序`
* `order by a desc, b			--a降序 b升序`
* `order by a desc, b desc	--a和b都是降序`


文字描述：

* 如果不制定排序的标准，则默认是升序。升序用`asc`表示，默认可以不写
* 为一个字段制定的排序标准并不会对另一个字段产生影响
* 强烈建议为每一个字段都指定排序的标准












