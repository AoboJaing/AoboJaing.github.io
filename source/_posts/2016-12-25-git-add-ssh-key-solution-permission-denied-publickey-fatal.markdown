---
layout: post
title: "Git(GitHub) 005 添加SSH密钥 — 解决：Permission denied (publickey) fatal The remote end hung up unexpectedly 问题"
date: 2016-12-25 15:27:00 +0800
comments: true
sharing: true
categories: [git_github]
tags: [git, github, ssh密钥, Permission denied (publickey)]
---


----------

当你下载一个源代码的时候。出现下面错误：

```
ubuntu@ubuntu:~/catkin_ws/src$ git clone git@github.com:turtlebot/turtlebot.git
Cloning into 'turtlebot'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
ubuntu@ubuntu:~/catkin_ws/src$ 
```

此时需要添加SSH密钥。步骤如下：

参考网址：[Generating an SSH key](https://help.github.com/articles/generating-an-ssh-key/)

## 步骤

先检查现有的SSH密钥

```
ls -al ~/.ssh
```
输出：

```
total 12
drwx------  2 ubuntu ubuntu 4096 Dec 24 07:40 .
drwxrwxr-x 32 ubuntu ubuntu 4096 Dec 24 07:29 ..
-rw-r--r--  1 ubuntu ubuntu  884 Dec 24 07:40 known_hosts
```


默认的，公钥的文件名可能是下面的几个：

```
id_dsa.pub
id_ecdsa.pub
id_ed25519.pub
id_rsa.pub
```

如果你现在没有公有的或者私有的钥匙，或者你不希望使用现有的任何一个去连接GitHub，这个时候，你可以去生成一个新的SSH密钥（SSH key）

如果你在上面的输出中看到了现有的公有和私有的密钥（比如： `id_rsa.pub` 和 `id_rsa`），这个时候，你可以直接连接GitHub，你可以将你的SSH密钥添加到ssh-agent。

## 生成一个新的SSH密钥（SSH key）

当你查看了你现有的密钥后没有SSH密钥，现在你可以来生成一个新的SSH密钥，用来身份验证。然后在将它添加到ssh-agent。


添加你的GitHub使用的e-mail地址：

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

这是会创建一个新的SSH密钥，使用提供的电子邮件作为标签。

```
Generating public/private rsa key pair.
```

此时提示你：“输入一个用来保存钥匙的文件”，默认保存在`/Users/you/.ssh/id_rsa`,我们直接按回车键。（它保存的位置跟你当前路径没有关系，默认都是保存在`~/.ssh/id_rsa`路径（即`/home/ubuntu/.ssh/id_rsa`）里面。）

```
Enter file in which to save the key (/home/ubuntu/.ssh/id_rsa): 
```

接下来，它提示你输入密码短语(passphrase)，如果你直接按回车，就是没有密码。我们可以输入`123456`：（详细的信息：[这里](Working%20with%20SSH%20key%20passphrases)）

```
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```

现在，密钥就生成了。

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482649196486.png)


----------

如果你不想在每次都使用你的SSH密钥重新输入你的密码短语，现在，你需要将你的密钥添加到SSH 代理（SSH Agent）中，它会管理你的SSH密钥，并记住你的密码短语。


----------

添加你的密钥（SSH key）到ssh-agent


在你添加一个新的SSH密钥到ssh-agent去管理你的密钥之前，我们查看一下当前新生成的密钥：

```
ls -al ~/.ssh
```

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482569573667.png)


----------

现在启动 ssh-agent（SSH代理），如果它还没有运行的话。

```
# start the ssh-agent in the background
$ eval "$(ssh-agent -s)"
Agent pid 2117
```

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482569662050.png)

这个时候，将你的SSH密钥添加到 ssh-agent。

```
ssh-add ~/.ssh/id_rsa
```

如果你你给你的SSH密钥设置了密码短语，你需要在输出提示`Enter passphrase for /home/ubuntu/.ssh/id_rsa:`时，输入密码短语（passphrase ）。

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482570315247.png)


## 将SSH密钥添加到你的GItHub账户上

参考网址：[Adding a new SSH key to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/#platform-linux)


为了配置你的GitHub账户去使用你的新的SSH密钥，你需要将SSH密钥添加到你的GitHub账户上。

第一步：复制共有密钥到剪切板上：


```
$ sudo apt-get install xclip
# 下载并安装 xclip. 如果你没有 `apt-get` 工具, 你可以使用其他的下载工具 (比如 `yum`)

$ xclip -sel clip < ~/.ssh/id_rsa.pub
# 复制 id_rsa.pub 文件里面的内容到你的剪切板里
```

> 注意，如果`xclip`工具不工作， 你可以直接手动复制。
>  
>  ![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482570795686.png)
>   
>   `cat ~/.ssh/id_rsa.pub`
>   
>   ![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482570885700.png)

再任何一个GitHUb页面右上角 你的用户图标 -> Settings ：

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482570974088.png)


在用户设置侧边栏中，点击**SSH and GPG keys**

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482571005369.png)


点击 **New SSH key**

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482571081262.png)


输入这个SSH密钥的标题 和 公有密钥，然后点击 **Add SSH key**：

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482649285303.png)


输入GitHub账户的密码：

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482571212784.png)


添加成功：

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482571232023.png)

## 测试你的SSH连接

参考网站：[Testing your SSH connection](https://help.github.com/articles/testing-your-ssh-connection/)

```
ubuntu@ubuntu:~$ ssh -T git@github.com
Warning: Permanently added the RSA host key for IP address '192.30.253.113' to the list of known hosts.
Hi AoboJaing! You've successfully authenticated, but GitHub does not provide shell access.
ubuntu@ubuntu:~$
```


## 成功了。



我们现在再来重新测试最上面的命令：

```
git clone git@github.com:turtlebot/turtlebot.git
```

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482574855747.png)

>  如果你在之前创建密钥的时候，给密钥添加的密码短语的话，在你执行`git clone XXX`的时候可能会让你输入密码短语：
>   
>  `Enter passphrase for key '/home/ubuntu/.ssh/id_rsa': `


你现在可能会发现，下载速度好像有点慢啊。如何给Git提速呢。请参考[这篇博客](http://www.aobosir.com/blog/2016/12/25/git-config-agent-purpose-clone-download-speed-up/)。

----------

当你使用了git，在你的GitHub账号的SSH keys管理的页面里面，可以看到：（它变绿了。）

![Alt text](/images/2016-12-25-git-add-ssh-key-solution-permission-denied-publickey-fatal/1482572823425.png)


----------

你现在可以执行下面的命令，查看当前你的git的配置。

```
ubuntu@ubuntu:~/catkin_ws/src$ git config --list
ubuntu@ubuntu:~/catkin_ws/src$ 
```

如果里面什么都没有，想我现在这个样子。你可以去完善你的git配置。请参考[这个网页](https://help.github.com/articles/set-up-git/#platform-linux)。


----------


