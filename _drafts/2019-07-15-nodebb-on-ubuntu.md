---
layout: post
title: 搭建基于 NodeBB 的论坛
---

通过阅读你能了解到：
1. 建立 sudo 权限账号；
2. 准备 NodeBB 运行环境；
3. 初次启动 NodeBB 时的配置；
4. 恢复上次运营的备份数据。

——此处有人家，云深缘浅，不得见。

<!--more-->

# 搭建基于 NodeBB 的论坛
网上有大批大批的论坛模板，为何偏偏选择 NodeBB 呢？

主要还是喜欢它的可定制化，并且里面涉及 NodeJS 系列技术非常之多，足够我学习很长的一段时间。


## 1. 建立 sudo 权限账号
使用 `useradd <username>` 命令创建用户，发现没有任何提示信息，于是使用 `userdel <username>` 命令删除后，改用 `adduser <username>` 创建新用户。

参考：[adduser 命令——菜鸟教程][1]。

随后切换到 root 用户，在 `/etc/sudoers` 中的 `root    ALL=(ALL:ALL) ALL` 这一行下，添加：
```text
<username> ALL=(ALL:ALL) ALL
```

再保存修改即可。

如果没有写权限，请使用 `chmod u+w /etc/sudoers` 授予，完成后再使用 `chmod u-w /etc/sudoers` 撤销。

另外，一个比较好的做法是在 `/etc/sudoers.d` 目录下，添加 `<username>` 文件，随后写入：
```text
<username> ALL=(ALL:ALL) ALL
```

保存后切换到此账户即可拥有 `sudo` 权限，而不需要修改系统文件。


## 2. 准备 NodeBB 运行环境
参考文档：[install on ubuntu][2]。

### 2.1 安装 Node.js
Node.js 是 NodeBB 运行时环境，就如同 JRE 是 Java 程序的运行时环境一样。

设置二进制发行库地址：
```bash
$ curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
```

设置完成：

![](/assets/images/nodebb/nodejs-repository.png)

安装 Node.js 程序：
```bash
$ sudo apt-get install -y nodejs
```

安装完成：

![](/assets/images/nodebb/nodejs-install.png)

验证所安装的版本：
```bash
$ node -v
v10.15.3
$ npm -v
6.4
```

验证结果如图：

![](/assets/images/nodebb/nodejs-verity.png)

### 2.2 安装 Redis
Redis 是一款性能强大的内存数据库，同时支持数据同步写入到磁盘，具备持久化功能。

切换到 root 用户，开始设置地址：
```bash
add-apt-repository ppa:chris-lea/redis-server
```

可能需要安装：

![](/assets/images/nodebb/install-software-properties-common.png)

按照提示执行：
```bash
apt install software-properties-common
```

继续设置 Redis 仓库：

![](/assets/images/nodebb/redis-repository.png)

开始安装：
```bash
apt-get update
apt-get install -y redis-server
```

安装完成：

![](/assets/images/nodebb/redis-install.png)

测试连接 Redis 数据库：
```bash
redis-cli
```

成功连接：

![](/assets/images/nodebb/redis-cli.png)

### 2.3 安装 NodeBB
NodeBB 是一款优秀的论坛模板，它的源代码托管在 GitHub 上，所以我们要通过 Git 从 GitHub 上拉取最新代码。

切回普通用户账号，安装 Git 版本管理工具：
```bash
sudo apt-get install -y git
```

安装成功：

![](/assets/images/nodebb/git-install.png)

拉取 NodeBB 源码到 `/home/<username>` 目录：
```bash
$ git clone -b v1.12.x https://github.com/NodeBB/NodeBB.git nodebb
$ cd nodebb
```

**注意：如果你的论坛由多个用户管理，切记不要安装在私人目录，最好放在 `/usr/local` 目录里。**

安装 NodeBB：
```bash
$ ./nodebb setup
```






[1]:https://www.runoob.com/linux/linux-comm-adduser.html
[2]:https://docs.nodebb.org/installing/os/ubuntu/