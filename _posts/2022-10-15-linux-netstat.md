---
layout:       post
title:        "Linux netstat命令"
author:       "HuFYy"
header-style: linux
catalog:      true
tags:
    - Linux
    - netstat

---

## Linux netstat命令

Linux netstat 命令用于显示网络状态。

利用 netstat 指令可让你得知整个 Linux 系统的网络情况。

### 语法

```
netstat \[-acCeFghilMnNoprstuvVwx\]\[-A<网络类型>\]\[--ip\]
```

**参数说明**：

+   \-a或--all 显示所有连线中的Socket。
+   \-A<网络类型>或--<网络类型> 列出该网络类型连线中的相关地址。
+   \-c或--continuous 持续列出网络状态。
+   \-C或--cache 显示路由器配置的快取信息。
+   \-e或--extend 显示网络其他相关信息。
+   \-F或--fib 显示路由缓存。
+   \-g或--groups 显示多重广播功能群组组员名单。
+   \-h或--help 在线帮助。
+   \-i或--interfaces 显示网络界面信息表单。
+   \-l或--listening 显示监控中的服务器的Socket。
+   \-M或--masquerade 显示伪装的网络连线。
+   \-n或--numeric 直接使用IP地址，而不通过域名服务器。
+   \-N或--netlink或--symbolic 显示网络硬件外围设备的符号连接名称。
+   \-o或--timers 显示计时器。
+   \-p或--programs 显示正在使用Socket的程序识别码和程序名称。
+   \-r或--route 显示Routing Table。
+   \-s或--statistics 显示网络工作信息统计表。
+   \-t或--tcp 显示TCP传输协议的连线状况。
+   \-u或--udp 显示UDP传输协议的连线状况。
+   \-v或--verbose 显示指令执行过程。
+   \-V或--version 显示版本信息。
+   \-w或--raw 显示RAW传输协议的连线状况。
+   \-x或--unix 此参数的效果和指定"-A unix"参数相同。
+   \--ip或--inet 此参数的效果和指定"-A inet"参数相同。

### 实例

显示详细的网络状况

```
# netstat -a
```

显示当前用户UDP连接状况

```
# netstat -nu
```

显示UDP端口号的使用情况

```
ubuntu@instance-1:~$  netstat -apu
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
udp        0      0 localhost:323           0.0.0.0:*                           -                   
udp        0      0 localhost:ipsec-nat-t   0.0.0.0:*                           -                   
udp        0      0 instance-1.:ipsec-nat-t 0.0.0.0:*                           -                   
udp        0      0 instance-1:ipsec-nat-t  0.0.0.0:*                           -                   
udp        0      0 0.0.0.0:ipsec-nat-t     0.0.0.0:*                           -                   
udp        0      0 localhost:isakmp        0.0.0.0:*                           -                   
udp        0      0 instance-1.asia-:isakmp 0.0.0.0:*                           -                   
udp        0      0 instance-1:isakmp       0.0.0.0:*                           -                   
udp        0      0 0.0.0.0:isakmp          0.0.0.0:*                           -                   
udp        0      0 0.0.0.0:l2f             0.0.0.0:*                           -                   
udp        0      0 localhost:domain        0.0.0.0:*                           -                   
udp        0      0 instance-1.asia-:bootpc 0.0.0.0:*                           -                   
udp6       0      0 ip6-localhost:323       [::]:*                              -                   
udp6       0      0 [::]:ipsec-nat-t        [::]:*                              -                   
udp6       0      0 ip6-localhost:isakmp    [::]:*                              -                   
udp6       0      0 [::]:isakmp             [::]:*                              -           
```

显示网卡列表:

```
ubuntu@instance-1:~$ netstat -i
Kernel Interface table
Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
docker0   1500     2237      0      0 0          2421      0      0      0 BMU
ens4      1500   564780      0      0 0        589585      0      0      0 BMRU
lo       65536    17922      0      0 0         17922      0      0      0 LRU
```



显示监听的套接口:

```
ubuntu@instance-1:~$ netstat -i
Kernel Interface table
Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
docker0   1500     2237      0      0 0          2421      0      0      0 BMU
ens4      1500   564780      0      0 0        589585      0      0      0 BMRU
lo       65536    17922      0      0 0         17922      0      0      0 LRU
ubuntu@instance-1:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:6379          0.0.0.0:*               LISTEN     
tcp        0      0 localhost:36497         0.0.0.0:*               LISTEN     
tcp        0      0 localhost:domain        0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6699            0.0.0.0:*               LISTEN     
tcp6       0      0 [::]:6699               [::]:*                  LISTEN     
tcp6       0      0 ip6-localhost:6379      [::]:*                  LISTEN     
udp        0      0 localhost:323           0.0.0.0:*                          
udp        0      0 localhost:ipsec-nat-t   0.0.0.0:*                          
udp        0      0 instance-1.:ipsec-nat-t 0.0.0.0:*                          
udp        0      0 instance-1:ipsec-nat-t  0.0.0.0:*                          
udp        0      0 0.0.0.0:ipsec-nat-t     0.0.0.0:*                          
udp        0      0 localhost:isakmp        0.0.0.0:*                          
udp        0      0 instance-1.asia-:isakmp 0.0.0.0:*                          
udp        0      0 instance-1:isakmp       0.0.0.0:*                          
udp        0      0 0.0.0.0:isakmp          0.0.0.0:*                          
udp        0      0 0.0.0.0:l2f             0.0.0.0:*                          
udp        0      0 localhost:domain        0.0.0.0:*                          
udp        0      0 instance-1.asia-:bootpc 0.0.0.0:*                          
udp6       0      0 ip6-localhost:323       [::]:*                             
udp6       0      0 [::]:ipsec-nat-t        [::]:*                             
udp6       0      0 ip6-localhost:isakmp    [::]:*                             
udp6       0      0 [::]:isakmp             [::]:*                             
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     19740    /var/snap/lxd/common/lxd/unix.socket
unix  2      [ ACC ]     STREAM     LISTENING     480351   /run/user/1001/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     481434   /run/user/1001/bus
unix  2      [ ACC ]     STREAM     LISTENING     23201    /var/run/charon.ctl
unix  2      [ ACC ]     STREAM     LISTENING     481435   /run/user/1001/gnupg/S.dirmngr
unix  2      [ ACC ]     STREAM     LISTENING     228      @/org/kernel/linux/storage/multipathd
unix  2      [ ACC ]     STREAM     LISTENING     481436   /run/user/1001/gnupg/S.gpg-agent.browser
unix  2      [ ACC ]     STREAM     LISTENING     481437   /run/user/1001/gnupg/S.gpg-agent.extra
unix  2      [ ACC ]     STREAM     LISTENING     481438   /run/user/1001/gnupg/S.gpg-agent.ssh
unix  2      [ ACC ]     STREAM     LISTENING     481439   /run/user/1001/gnupg/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     481440   /run/user/1001/pk-debconf-socket
unix  2      [ ACC ]     STREAM     LISTENING     481441   /run/user/1001/snapd-session-agent.socket
unix  2      [ ACC ]     STREAM     LISTENING     23441    /run/containerd/containerd.sock.ttrpc
unix  2      [ ACC ]     STREAM     LISTENING     23443    /run/containerd/containerd.sock
unix  2      [ ACC ]     STREAM     LISTENING     14253    /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     14255    /run/systemd/userdb/io.systemd.DynamicUser
unix  2      [ ACC ]     STREAM     LISTENING     226      /run/lvm/lvmpolld.socket
unix  2      [ ACC ]     STREAM     LISTENING     231      /run/systemd/fsck.progress
unix  2      [ ACC ]     STREAM     LISTENING     235      /run/systemd/journal/stdout
unix  2      [ ACC ]     SEQPACKET  LISTENING     240      /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     304      /run/systemd/journal/io.systemd.journal
unix  2      [ ACC ]     STREAM     LISTENING     260006   /var/run/fail2ban/fail2ban.sock
unix  2      [ ACC ]     STREAM     LISTENING     264555   /run/pluto/pluto.ctl
unix  2      [ ACC ]     STREAM     LISTENING     27070    /var/run/docker/metrics.sock
unix  2      [ ACC ]     STREAM     LISTENING     26112    /var/run/docker/libnetwork/a8e17e446ed5.sock
unix  2      [ ACC ]     STREAM     LISTENING     19733    /run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     19737    /run/docker.sock
unix  2      [ ACC ]     STREAM     LISTENING     19741    /run/snapd.socket
unix  2      [ ACC ]     STREAM     LISTENING     19743    /run/snapd-snap.socket
unix  2      [ ACC ]     STREAM     LISTENING     19354    /run/uuidd/request
unix  2      [ ACC ]     STREAM     LISTENING     19739    @ISCSIADM_ABSTRACT_NAMESPACE
```

### 个人使用经验

```
ubuntu@instance-1:~$ netstat -antp
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.1:6379          0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.1:36497         0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:6699            0.0.0.0:*               LISTEN      -                   
tcp        0      0 10.170.0.2:34540        216.239.38.174:443      ESTABLISHED -                   
tcp        0      0 10.170.0.2:33602        216.239.38.174:443      ESTABLISHED -                   
tcp        0    352 10.170.0.2:6699         115.171.84.245:30617    ESTABLISHED -                   
```

```
ubuntu@instance-1:~$ netstat antp|grep 6699
tcp        0     64 instance-1.asia-ea:6699 115.171.84.245:30617    ESTABLISHED
tcp        0      0 instance-1.asia-ea:6699 115.171.84.245:30010    ESTABLISHED
```

### 参考

---

[菜鸟教程（netstat）](https://www.runoob.com/linux/linux-comm-netstat.html)


