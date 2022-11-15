---
layout:       post
title:        "Linux配置密钥登陆"
author:       "HuFYy"
header-style: " \"Hello World, Hello Blog\""
catalog:      true
tags:
    - Linux
    - SSH  

---

### 1.使用ssh-keygen命令生成公钥和私钥

```shell
ubuntu@VM-8-6-ubuntu:~$ ssh-keygen 
Generating public/private rsa key pair.
# 此处选择密钥文件保存的路径
Enter file in which to save the key (/home/ubuntu/.ssh/id_rsa): 
# 此处输入密钥的密码，如果不需要输入密码，连按两次回车即可
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/ubuntu/.ssh/id_rsa
Your public key has been saved in /home/ubuntu/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:L5DG8JxsLmXuTOTNlmwACbICOiWwAsZFJuA2O8GlqLQ ubuntu@VM-8-6-ubuntu
The key's randomart image is:
+---[RSA 3072]----+
|@o==             |
|OB=. .           |
|OO  +            |
|*.=  B o         |
|.E    / S        |
|  .  X * o       |
|    . = O .      |
|     = o .       |
|      o          |
+----[SHA256]-----+
```

**通过ftp或其他文件传输工具将id_rsa文件导出，或者直接复制id_rsa文件的内容到你的本地。**

**其中id_rsa文件为私钥，id_rsa.pub为公钥。**

### 2.将id_rsa文件中的内容重定向到authorized_keys文件中，并修改权限

```shell
cd ~/.ssh/
cat id_rsa.pub >> authorized_keys
chmod 600 authorized_keys
chmod 700 ~/.ssh/
```

### 4.修改ssh服务端的配置文件

**ssh服务端的配置文件路径为：**`/etc/ssh/sshd_config`

```shell
将PubkeyAuthentication no改为yes并取消注释
将AuthorizedKeysFile  .ssh/authorized_keys .ssh/authorized_keys2取消注释
将PasswordAuthentication yes改为no并取消注释
```

### 5.重启ssh服务

`systemctl restart sshd`

在重启ssh服务之前最好先建立一个ssh连接，防止配置错误导致连接失败。

### 6.重新连接ssh

在你的本地打开命令行执行以下命令

`ssh -i "第一步拷贝出来的私钥文件的路径" 你的用户名@你的IP地址`

按照提示输入密码即可完成连接。
