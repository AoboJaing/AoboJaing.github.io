---
layout: post
title: "SQL 数据库 解决问题：无法打开物理文件 \"XXX.mdf\"。操作系统错误 5:\"5(拒绝访问。)\"。 (Microsoft SQL Server，错误: 5120) --- 附加数据库时出错。有关详细信息，请单击“消息”列中的超链接。"
date: 2016-10-16 18:52:33 +0800
comments: true
sharing: true
categories: [SQL, SQL Server]
tags: [SQL, SQL Server, 拒绝访问, 操作系统错误, 无法打开物理文件, 错误 5120]
---


---

* 我的电脑系统：**Windows  10** 64位
* **SQL Server** 软件版本： **SQL Server 2014 Express**

---

## 出现的问题

在你 **附加**  一个外部数据库到服务器上是，出现下面的错误：


![Alt text | center](/images/2016-10-16-SQL-Solve-problem-Microsoft-SQL-Server-error-5120/1476612776678.png)

![Alt text | center](/images/2016-10-16-SQL-Solve-problem-Microsoft-SQL-Server-error-5120/1476612808460.png)

---

## 解决办法


1.       找到要附加的`.mdf`文件--------->右键--------->属性--------->安全--------->选择当前用户--------->编辑--------->完全控制。
	* ![Alt text](/images/2016-10-16-SQL-Solve-problem-Microsoft-SQL-Server-error-5120/1476613072444.png)
	* ![Alt text](/images/2016-10-16-SQL-Solve-problem-Microsoft-SQL-Server-error-5120/1476613183163.png)


2.       对.`log`文件进行相同的处理。


---

## 搞定

---


参考网站：

http://blog.csdn.net/justdb/article/details/8457487
