# Jekyll

官方简介：

> Transform your plain text into static websites and blogs.

文档传送门：[Jekyll][1]。

**个人总结：发布和托管个人博客/项目文档的最佳工具。**

## 一、简单步骤

### 1.1 [安装 Ruby 开发环境][2]

- 需要 Ruby 2.4.0 或更高版本，请运行 `ruby -v` 和 `gem -v` 检查。

- 需要 GCC 和 Make，请运行 `gcc -v`、`g++ -v` 和 `make -v` 检查。

### 1.2 安装 Jekyll 和 [bundler][3] [gems][4]

```bash
gem install jekyll bundler
```

### 1.3 创建新的 Jekyll 网站

```bash
jekyll new myblog
```

### 1.4 本地预览

在 myblog 文件夹中：
```bash
bundle exec jekyll serve
```

运行成功后在浏览器中打开：
```text
http://localhost:4000
```

## 二、[WSL][6] 环境实战

非 [WSL][6] 环境可以跳过这部分内容。

### 2.1 更新 repo 列表和包 

```bash
sudo apt-get update -y && sudo apt-get upgrade -y
```

### 2.2 使用 [BrightBox][7] 安装 Ruby 优化版本

```bash
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf
```

### 2.3 更新 Ruby Gems 并安装 Jekyll

```bash
gem update

gem install jekyll bundler

jekyll -v
```

注意：这里不用 `sudo`。

有关更多内容，请参考：[Jekyll on Windows][5]。



[1]:https://jekyllrb.com/
[2]:https://www.ruby-lang.org/en/downloads/
[3]:https://jekyllrb.com/docs/ruby-101/#bundler
[4]:https://jekyllrb.com/docs/ruby-101/#gems
[5]:https://jekyllrb.com/docs/installation/windows/
[6]:https://msdn.microsoft.com/en-us/commandline/wsl/about
[7]:https://www.brightbox.com/docs/ruby/ubuntu/