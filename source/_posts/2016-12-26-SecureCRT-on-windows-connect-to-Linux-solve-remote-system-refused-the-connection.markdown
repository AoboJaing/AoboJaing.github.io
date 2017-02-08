---
layout: post
title: "Windows上使用SecureCRT软件连接Linux终端 — 解决问题；The remote system refused the connection"
date: 2016-12-26 01:46:45 +0800
comments: true
sharing: true
categories: [Linux]
tags: [Windows, The remote system refused the connection, SecureCRT, Linux, ssh-agent]
---


----------
 
## 正常的情况：

```
ifconfig
```

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552549436.png)

```
whoami
```

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552591430.png)

```
ps -e | grep ssh
```

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552750155.png)


----------

**secureCRT**软件

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552633225.png)

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552666663.png)

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552793582.png)

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552803114.png)


----------

## 不正常的情况：The remote system refused the connection.



如果你遇到这个问题，说明你的Linux系统里面没有安装`openssh-server`

```
sudo apt-get install openssh-server
```

```
aobosir@ubuntu:~$ ps -e | grep ssh
 3834 ?        00:00:00 sshd
```


执行完下面的命令，系统会自动注销（Logout）。

```
ssh-agent restart
# 已经没有这个命令了。替代的方法就是:重启系统或者注销系统。
```

----------

现在查看一下，现在就可以进入了正常使用的状态。


```
aobosir@ubuntu:~$ ps -e | grep ssh
 3834 ?        00:00:00 sshd
 4116 ?        00:00:00 ssh-agent
aobosir@ubuntu:~$ 
```

----------

现在，我们在Windows系统这段使用**SecureCRT**软件连接这个Linux系统，就可以添加成功了。

连接成功之后，我们现在在**SecureCRT**软件连接的Linux系统终端中再次下面命令来查看当前运行着的**ssh**进程有哪些。（现在，我们已经可以在Windows端的**SecureCRT**软件里面控制Linux端了。）

```
ps -e | grep ssh
```

查看**Linux**这端的当前进程：（正常你会看大下面的4个。（我也不知道是什么东西））

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552750155.png)


## 搞定

----------



参考网站：http://blog.csdn.net/lifengxun20121019/article/details/13627757
