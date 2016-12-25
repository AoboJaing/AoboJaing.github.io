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


```
ssh-agent restart
```

执行完这个语句，系统会自动注销（Logout）。

```
aobosir@ubuntu:~$ ps -e | grep ssh
 3834 ?        00:00:00 sshd
 4116 ?        00:00:00 ssh-agent
aobosir@ubuntu:~$ 
```


刚刚还不正常的，现在有好使了。再次查看**Linux**当前进程：（下图是正常的情况，如果你看到这样的结果，说明Linux端已经没有问题了，SSH-Agent已经正常的运行了。）

![Alt text](/images/2016-12-26-SecureCRT-on-windows-connect-to-Linux-solve-remote-system-refused-the-connection/1482552750155.png)

参考网站：http://blog.csdn.net/lifengxun20121019/article/details/13627757
