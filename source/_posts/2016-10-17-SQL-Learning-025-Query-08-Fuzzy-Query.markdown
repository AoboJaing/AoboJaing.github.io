---
layout: post
title: "SQL 数据库 学习 025 查询-08 模糊查询 ---  怎样编写模糊查询语句"
date: 2016-10-17 06:59:39 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 查询, 模糊查询]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

> 本篇博客里面使用了 `scott` 库，如何你现在还没有添加这个库到你的服务器里面，请在查看本篇博客前，访问[这篇博文](http://www.aobosir.com/blog/2016/10/16/SQL-Learning-016-how-to-attach-a-database/)来在你的服务器里面附加`scott`库。

---


## 怎样编写模糊查询语句

```sql
select * from emp where ename like '%A%'
	--ename只要含有字母A就输出
select * from emp where ename like 'A%'
	--ename只要首字母是A的就输出
select * from emp where ename like '%A'
	--ename只要尾字母是A的就输出
```

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658355448.png)

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658371703.png)

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658389550.png)

---

```sql
select * from emp where ename like '_A%'
	--ename只要第二个字母是A的就输出
```

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658413951.png)


---

```sql
select * from emp where ename like '_[A-F]%'
	--把ename中第二个字符是A或者B或者C或者D或者E或者F的记录输出
```

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658456248.png)


---

```sql
select * from emp where ename like '_[^A-F]%'
	--把ename中第二个字符不是A也不是B也不是C也不是D也不是E也不是F的记录输出
```

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658507717.png)


---

创建一个 `student` 表。（预备操作）

```sql
create table student
(
	name nvarchar(20) null,
	age int
);

insert into student values ('张三', 68);
insert into student values ('Tom', 66);
insert into student values ('a_b', 22);
insert into student values ('c%d', 44);
insert into student values ('abc_fe', 56);
insert into student values ('haobin', 25);
insert into student values ('HapBin', 88);
insert into student values ('c%', 66);
insert into student values ('long''s', 100)

select * from student;
```

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658533004.png)

---

```sql
select * from student where name like '%\%%' escape '\'
	--把name中包含有%的输出
select * from student where name like '%\_%' escape '\'
	--把name中包含有_的输出
```

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658590460.png)

![Alt text](/images/2016-10-17-SQL-Learning-025-Query-08-Fuzzy-Query/1476658616954.png)

---


**总结：** **通配符：**

**格式：** `select 字段的集合 from 表名 where 某个字段的名字 like 匹配的条件`

> 匹配的条件通常含有通配符


* `%`
	* 表示任意0个或多个字符
* `_` （这个是下划线，不是减号）
	* 表示任意单个字符
* `[a-f]`
	* `a` 到 `f` 中的任意单个字符。只能是`a`、`b`、`c`、`d`、`e`、`f` 中的任意一个字符
* `[a, f]`
	* `a` 或者 `f`
* `[^a-c]`
	* 不是`a`、也不是`b`，也不是`c`的任意单个字符


---

**注意：** 

* 匹配的内容必须使用单引号括起来。不能省略，也不能改用双引号。 
* `escape '\'` 里面 `escape` 后面 `''` 里面的`\` 字符就自定义的：通配符。它可以替换成其他的字符（比如：`a`、`b`、`m` 等等）。


---



