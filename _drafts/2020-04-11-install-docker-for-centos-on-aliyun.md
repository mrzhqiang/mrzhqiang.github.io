---
layout: post
title: GitLab | 在 Centos7.6 上使用 Docker 安装
---

# 先决条件
全新购买的阿里云服务器，操作系统 Centos7.6 64位。

```text
  2 vCPU 8 GiB (I/O优化)，ecs.g6.large 100Mbps (峰值)
```

刚配置好的操作系统镜像，纯天然无污染。

# 一、yum 加速
参考：[yum源加速](https://www.jianshu.com/p/b7cd2f9fb8b7)。

# 二、安装 docker
参考：[Install Docker Engine on CentOS](https://docs.docker.com/engine/install/centos/)。

启动，测试可行性：
```bash
sudo systemctl start docker

sudo docker run hello-world
```

# 三、Docker 镜像加速器
通常每个阿里云控制台中，都会带有一个镜像加速器。

```bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://gdtonbpy.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

# 四、（可选）挂载数据盘
参考：[阿里云数据盘挂载完整过程](https://www.jianshu.com/p/fa587bbfbb60)。

# 五、Docker 安装 GitLab
参考 [GitLab 官方文档](https://docs.gitlab.com/omnibus/docker/README.html)。

## 5.1 设置 GitLab 主目录
```bash
export GITLAB_HOME=/srv
```

## 5.2 使用 Docker 安装
```bash
sudo docker run --detach \
  --hostname [IP 或域名] \
  --publish 443:443 --publish [外网访问端口:80] --publish 8022:8022 \
  --name gitlab \
  --restart always \
  --volume $GITLAB_HOME/gitlab/config:/etc/gitlab \
  --volume $GITLAB_HOME/gitlab/logs:/var/log/gitlab \
  --volume [数据盘路径]:/var/opt/gitlab \
  gitlab/gitlab-ce:latest
```

注意：通常 22 端口都会被占用，所以改在 8022 端口上。这个改动可能导致其他问题，待会再看看。

## 5.3 配置外部 URL
首先进入 Docker 控制台：
```bash
sudo docker exec -it gitlab /bin/bash
```

然后找到 `/etc/gitlab/gitlab.rb` 文件，编辑内容为：
```bash
external_url = '[服务器 IP 地址或域名:外网访问端口]'
```

保存后，重启一下：
```bash
sudo docker restart gitlab
```

# 六、从外网访问 GitLab
浏览器首次访问 GitLab 会要求修改密码，随后可以使用 root + 密码登录 GitLab 后台。
