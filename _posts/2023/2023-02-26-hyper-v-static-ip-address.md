---
layout: post
title: Hyper-v | 静态 IP 地址
---

使用 win10+ 系统自带的 Hyper-v 虚拟机创建多个 Centos7.9 系统，每次重启 IP 地址都会发生变化，为此，需要设置静态 IP 地址。

<!--more-->

# 背景
通过 win11 的 Hyper-v 管理器创建了三台 Centos7.9.2009 系统，由于 Hyper-v 自带的连接器不好用，所以在 win11 宿主机中安装了 XShell7 远程访问工具。

XShell7 可以设置远程会话列表，方便在不同的远程访问中快速切换，而且传输文件也很方便。

为了把虚拟机添加到远程会话列表，我们需要将三台虚拟机的 IP 地址固定下来，否则每次启动 IP 地址都不同，会话列表失去了意义。

# 网络设置

## 固定 IP
编辑网络设置文件：

```shell
cd /etc/sysconfig/network-scripts
vi ifcfg-eth0
```

修改或添加以下内容：

![ifcfg-eth0](/assets/images/hyper-v/ifcfg-eth0.png)

注意每台虚拟机要使用不同的 IPADDR 地址，其他配置则保持相同。