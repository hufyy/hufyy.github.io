---
layout:       post
title:        "Linux安装redis"
author:       "HuFYy"
header-style: redis
catalog:      true
tags:
    - Linux
    - redis
---
## Linux源码安装redis

**Redis下载地址：**http://redis.io/download，下载最新稳定版本。

本教程使用的Redis版本为 7.0.5，下载并安装：

```shell
wget https://github.com/redis/redis/archive/7.0.5.tar.gz
tar -zxvf 7.0.5.tar.gz
cd redis-7.0.5/
make
```

执行完 **make** 命令后，redis-7.0.5 的 **src** 目录下会出现编译后的 redis 服务程序 redis-server，还有用于测试的客户端程序 redis-cli：

下面启动 redis 服务：

```shell
cd src
./redis-server
```

上述方式是以默认方式启动redis，但是在大部分生产环境中是以配置文件来启动，启动方式如下：

```shell
cd src
./redis-server ../redis.conf
```

**redis.conf** 是一个默认的配置文件。我们可以根据需要使用自己的配置文件。

启动 redis 服务进程后，就可以使用测试客户端程序 redis-cli 和 redis 服务交互了。 比如：

```shell
cd src
./redis-cli
redis> set a b
OK
redis> get a
"b"
```

如果需要redis以守护进程方式运行，则需要修改redis配置文件：

```shell
vim ../redis.conf
将daemonize no修改为daemonize yes
```

### 参考

---

<https://www.runoob.com/redis/redis-tutorial.html>

— HuFYy

