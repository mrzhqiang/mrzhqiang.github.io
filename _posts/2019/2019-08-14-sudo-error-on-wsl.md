---
layout: post
title: 在 WSL 下登陆 root 账号
---

WSL 是 windows 10 下的一个 Linux 子系统，我们通常在 `WIN + R` 中使用 `bash` 或 `ubuntu`（对应系统名称）登陆这个子系统，但我想用 root 账号去做一些事情时，对于 `su root` 我并不知道正确的密码。
当时我是为了解决某个家伙（就是你，Ruby Gem！）反复提示的权限警告，按照惯例，我修改了 `/etc/sudoers` 文件，并强制覆盖保存，随后我的 `sudo` 命令再也不能使用，在修复这个问题时，我发现了在 WSL 中 root 账号的秘密。

<!--more-->

# WSL 简介
关于 WSL 的有关内容，请参考我在简书上的博客：[WSL][1]。

# 遇到的问题
当我使用 `sudo` 作为相关命令的前缀时，我遇到的这个错误：

```bash
>>> /etc/sudoers: syntax error near line 30 <<<
sudo: parse error in /etc/sudoers near line 30
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
```

于是我想查看 `/etc/sudoers` 文件的第 30 行内容：

```bash
cat sudoers
```

提示我权限不足：

```bash
cat: sudoers: Permission denied
```

按照正常逻辑，加上 `sudo` 前缀，又回到了最初的错误。

在正常的 Ubuntu 系统中，对于 `/etc/sudoers` 的错误，通过以下命令解决：

```bash
cd /etc
pkexec visudo
```

但是我这个是 WSL 环境，在运行上面的解决方案时，出现提示：

```bash
Error getting authority: Error initializing authority: Could not connect: No such file or directory
```

于是我不得不去求助搜索引擎，经过查阅得知，对于 WSL 而言，可以在 CMD 或者 Windows PowerShell 中使用以下命令登陆 root 账号：

```bash
wsl -u root
```

*参考：[sudoers-file-syntax-error-on-wsl][2]。*

随后修复 `/etc/sudoers` 文件的第 30 行内容，再测试 `sudo` 命令：

```bash
sudo apt update
```

一切都回归正常。

# 举一反三
我忽然想到这是 WSL，对于修改文件这种事情，Windows 用户是最有权限的，而我只需要找到 WSL 的路径即可。

WSL 的根目录路径通常位于：

```
C:\Users\<username>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_<systemname>\LocalState\rootfs
```

随后使用记事本打开 `etc` 目录下的 `sudoers` 文件，修改后保存，再进入 WSL 查看，保存成功！


# 总结
果然换个思路，解决问题的办法就会简单很多，但搜索引擎告诉我的方法更有价值，因为我一直想 `su root` 而得不到解决办法，没想到今天发现了秘密。



[1]:https://www.jianshu.com/p/0cce34befb51
[2]:https://askubuntu.com/questions/1144326/sudoers-file-syntax-error-on-wsl
