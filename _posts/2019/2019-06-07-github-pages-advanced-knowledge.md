---
layout: post
title: 搭建 GitHub Pages 博客：二、进阶知识
---

通过阅读你能了解到：
1. 掌握 GitHub Pages 规则；
2. 使用 Jekyll 本地预览；
3. 学习 Markdown 语法；
4. 接触 Git 概念。

——意尽而知其然，思深则所以然。

<!--more-->

# 进阶知识
我知道世界上有很多值得去的地方，我也知道写博客的地方有很多，但我就喜欢自定义，也只认可自己的风格，这就是我。

## 1. 掌握 GitHub Pages 规则
从仓库设置的 GitHub Pages 选项中，找到 [学习更多][1] 按钮：

![](/assets/images/github-pages/pages-learn-more.png)

通过 [学习更多][1]，了解到以下要点：
- 允许在以下分支或文件夹发布站点：
  - `master` 分支
  - `gh-pages` 分支
  - `master` 分支下的 `/docs` 文件夹
- 如果仓库名是 `<username>.github.io`（个人博客），则只能从 `master` 分支发布。
- `/docs` 文件夹也只能从 `master` 分支发布。

如果没有以上任何分支或文件夹，那么站点将被设置为“无”：

![](/assets/images/github-pages/none-source-setting.png)

在 [学习更多][1] 中有一句话：
> For more information about the different types of GitHub Pages sites, see "[User, Organization, and Project Pages][2]."

想要查看关于 GitHub Pages 站点不同类型的更多信息，参见：[用户、组织和项目页面][2]。

不同类型站点的区别：
- 项目页面：任何项目都可以有一个站点页面，作为 API 文档，或项目文档，或门户网站，等等等等。
- 用户、组织页面：与项目页面几乎相同，可以认为是特殊的项目页面，但也有重要的区别：
  - 项目页面属于特定项目，用户、组织页面属于顶级域名的专属项目。
  - 访问项目页面时，需要提供用户、组织页面的顶级域名，比如：`<username>.github.io/<project>`。

在 [用户、组织和项目页面][2] 中有个小提示：
> Tip: GitHub Pages sites are always publicly accessible when published, even if their repository is private, and they shouldn't be used for sensitive transactions like sending passwords or credit card numbers. For more information, see "[What is GitHub Pages?][3]"

这就是我想要的 [什么是 GitHub Pages][3]，点进去看看：

> GitHub Pages is a static site hosting service designed to host your personal, organization, or project pages directly from a GitHub repository.

简单来说，[GitHub Pages][20] 就是个人、组织或项目主页的托管服务。

[GitHub Pages][20] 的使用限制：
- 源仓库大小建议限制为 1GB，包括作为静态网站的文件。
- 网站的每月访问流量被限制为 100GB，这是一个软带宽限制。
- 每小时提交到 [GitHub Pages][20] 的版本限制为 10 个，这也是一个软限制。

如果有兴趣了解更多，请参考：[GitHub Pages 基础知识][4]。


## 2. 使用 Jekyll 本地预览
在 [什么是 GitHub Pages][3] 文章末尾找到 [超越 GitHub Pages 基础][5]：

![](/assets/images/github-pages/beyond-github-pages-basics.png)

点进去之后，我找到了我想要的 [自定义 GitHub Pages][6]：

![](/assets/images/github-pages/custom-github-pages.png)

### 2.1 发现 Jekyll

对于 [自定义 GitHub Pages][6]，目前我们只需要关心这些内容：

![](/assets/images/github-pages/jekyll-as-static-site-generator.png)

首先查看 [关于 GitHub Pages 和 Jekyll][7] 的简介：
> GitHub Pages is deeply integrated with [Jekyll][8], a popular static site generator designed for blogging and software documentation, but used for much more.

翻译：GitHub Pages 与 [Jekyll][8] 深度集成，[Jekyll][8] 是一款专门为博客和软件文档设计的流行静态站点生成器，但它也用于更多场景。

[Jekyll][8] 的主要优点：
- 使用 [Markdown][10]，而不是 HTML。[Markdown][10] 易于读写。
- 就像前面我们所做的那样，无需 css 文件即可更换博客主题。
- 通过 [Jekyll 主题选择器][11] 快速创建新网站。
- 使用模板定制页眉页脚，以及其他重复布局，让创作只关注它本身。
- 最简单的构建站点过程（这一点我们在新手入门已经领略到）。

文章的末尾，我们找到 [Jekyll 文档][9]：

![](/assets/images/github-pages/find-jekyll-documentation.png)

让我们进入 [Jekyll 文档][9] 看看：

![](/assets/images/github-pages/jekyll-home-page.png)

### 2.2 了解 Jekyll

Jekyll 官方简介：
> Transform your plain text into static websites and blogs.

翻译：将纯文本转换为静态网站和博客。

Jekyll 的三个特点：
- 简单：没有数据库，没有其他组件，不需要更新，只要写你的内容。
- 静态：集成 Markdown、Liquid、HTML 和 CSS，随时可以部署。
- 博客感知：永久链接、类别、页面、帖子和自定义布局是主要功能。

### 2.3 试运行

一秒安装运行：
```bash
~ $ gem install bundler jekyll
~ $ jekyll new my-awesome-site
~ $ cd my-awesome-site
~/my-awesome-site $ bundle exec jekyll serve
```

一般来说，有命名行命令或者安装步骤，我都喜欢先尝试一下：

![](/assets/images/github-pages/gem-install-jekyll-bundler.png)

*提示：你有可能会遇到 `gem` 命令未找到的错误，甚至根本不知道在哪里运行这条命令。没有关系，你先看着，后面会告诉你怎么解决这些问题。*

第一条命令“艰难”地运行成功，再看看第二条：

![](/assets/images/github-pages/jekyll-new-my-awesome-site.png)

依然向我申请了 `sudo` 权限，才得以成功安装。

继续执行后面的命令：

![](/assets/images/github-pages/bundler-exec-jekyll-serve.png)

然后打开浏览器，输入:`localhost:4000`，查看：

![](/assets/images/github-pages/look-up-my-awesome-site.png)

确实有够简单粗暴的，而且页面布局都已经弄好，就等我把里面的东西改一改，我的博客就可以上线了。

尝试了一秒安装运行之后，让我们从 [Jekyll DOCS][12] 开始本地预览：

![](/assets/images/github-pages/jekyll-docs.png)

### 2.4 安装完整的开发环境
Jekyll 是用 Ruby 写的，所以我们要在本地运行和预览，就必须安装 Ruby 开发环境：

![](/assets/images/github-pages/ruby-development-environment.png)

各种操作系统的安装指南：
- [macOS][13]
- [Ubuntu Linux][14]
- [Other Linux distros][15]
- [Windows][16]

*提示：由于我的电脑是 Windows 系统，因此其他操作系统请自行参考官方文档，我仅演示在 Windows 系统中的安装和运行。*

在 Windows 10 的 1607 版本之后，自带有一个 Linux 子系统，我们称之为：[WSL][17]。

通过使用 [WSL][17] 安装 Ubuntu 系统，我们就可以很嗨皮地在本地运行和预览 Jekyll 项目了。

安装 [GCC][18] 和 [Make][19]：
```bash
sudo apt-get install gcc g++ make
```

更新与升级 apt：
```bash
sudo apt-get update -y && sudo apt-get upgrade -y
```

安装 Ruby 开发环境：
```bash
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf
```

更新 Ruby 的包管理器 gem：
```bash
gem update
```

*提示：在 WSL 中需要 sudo 权限来操作 gem，因此这一条命令执行失败，你就需要这样运行：`sudo gem update`。*

安装 jekyll 和 bundler：
```bash
gem install jekyll bundler
```

*提示：同样可能需要 sudo 权限。*

安装完之后，你可以回头再看看前面的【试运行】部分，去创建属于你的博客网站吧。

## 3. 学习 Markdown 语法
在 Jekyll 的主要优点中，第一条就是它使用 [Markdown][10] 编写内容，所以我们去看一下：

![](/assets/images/github-pages/markdown-on-github.png)

只了解 [基本编写和格式化语法][21] 即可：

![](/assets/images/github-pages/markdown-basic-writing.png)

选项释义：
- `Headings`：标题，使用 `#` 表示一级标题，`##` 表示二级标题，以此类推，总共六级。
- `Styling text`：样式文本，实际上对应字体中的粗体、斜体、删除线以及嵌套的粗体和斜体。
- `Quoting text`：引用文字，就是对别人说过的话，进行引用，弥补自己的可信度。
- `Quoting code`：引用代码，可以在一句话里面单独引用，也可以作为完整的一段引用。
- `Links`：超链接，点击跳转到其他页面，甚至其他网站。
- `Section links`：片段链接，这是 Github 独有的渲染方式，可以跳转到基于标题的地方。
- `Relatice links`：相对链接，一些资源文件可以通过相对链接进行访问，比如图片、文档。
- `Lists`：列表，分为无序列表和有序列表，使用 `-` 或 `*` 表示无序，使用 `1.` 表示有序，列表可以嵌套多层。
- `Task lists`：任务列表，大多数 Markdown 渲染器都支持这个语法，使用 `[X]` 表示已完成，`[ ]` 表示未完成。

其他选项都不在这篇文章的范围内，所以也就不再继续讨论。

尝试使用 Markdown 语法更新一下主页：

![](/assets/images/github-pages/vim-index.png)

*提示：你可以选择任何你喜欢的文本编辑器，对 markdown 文件进行编辑，没错，任何文本编辑器。*

写入前面的那些选项：

![](/assets/images/github-pages/markdown-display-1.png)

一个屏幕放不下来，翻页继续：

![](/assets/images/github-pages/markdown-display-2.png)

看看最终效果：

![](/assets/images/github-pages/preview-my-awesome-site.png)

你可能已经注意到【删除线】那个地方，并没有正确显示，实际上它应该使用 `~~` 包裹起来，就像下面的例子一样：

~~删除线~~

有关 Markdown 的语法到此为止，想要了解更多细节，请参考：[Markdown 官方网站][22] 和 [Markdown 中文文档][23]。

这篇 [Markdown 快速入门][24] 博客里讲到使用 Markdown 制作流程图，也是非常厉害了。


## 4. 接触 Git 概念
[GitHub Pages 基础知识][4] 中第四条 [使用命令行创建项目页面][25] 展示了如何使用 Git 来下载和上传仓库源文件。

这就解决了一个问题：本地运行和预览的站点项目，如何部署到 GitHub 上并使用 GitHub Pages 托管？

然而有趣的是，正当我准备打开 [Git 官网][26] 时，它无论如何也不能访问。

这就是逼我用自己的语言描述有关 Git 的概念：
- 一种代码版本管理工具，最初用于 Linux 的源码开发维护。
- 随后被 Linux 之父开源出来，受到所有程序员的一致好评。
- GitHub 借助 Git 成为了世界上最大的开源社区。
- 开源精神由于 Git 的存在，得到发扬光大。
- 我也用 Git 管理我的所有项目，将它们上传到 GitHub 上。

一次正常的 Git + GitHub 流程：

通过 GitHub 创建仓库（这在上一篇文章中有提到）：

![](/assets/images/github-pages/create-github-repository.png)

获取这个仓库的克隆链接：

![](/assets/images/github-pages/github-quick-setup.png)

四种方式同步源码库：

1. 复制仓库地址，通过 Git 命令行工具克隆到本地，进行一系列修改、添加、提交，最后推送到 Github 上。

2. 本地初始化 Git 仓库，添加文件，提交改动，添加远程仓库地址，推送到远程仓库上。

3. 在已有的 Git 仓库中，添加远程仓库地址，然后推送到远程仓库上。

4. 从其他源码仓库导入到 GitHub 上。

Git 简单概念：

- `git clone <url>`：克隆远程仓库到本地。
- `git add .`：添加所有改动到暂存区。
- `git commit -m "<message>"`：提交所有暂存到最新版本。
- `git push`：推送所有本地版本到远程仓库。
- `git init`：在本地初始化一个 Git 仓库。
- `git remote add origin <url>`：添加远程仓库地址到本地仓库设置。
- `git push -u origin master`：推送本地 `master` 分支到远程仓库。

能掌握上面的这些命令，你就已经是一名合格的 Git 用户了。

现代 IDE 集成并简化了 Git 的相关操作，使得我们并不需要花费过多精力在这上面。

到这里，必须恭喜你，成功获得了 GitHub Pages 进阶知识。


# 总结
GitHub 托管你的博客站点，Jekyll 设计你的博客主题，GitHub Pages 渲染你的博客网页，Markdown 格式化你的博客内容，Git 管理你的博客仓库。

一切都很完美！但是，我想要的自定义样式，还需要更强大的工具。


[1]:https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages
[2]:https://help.github.com/en/articles/user-organization-and-project-pages
[3]:https://help.github.com/en/articles/what-is-github-pages
[4]:https://help.github.com/en/categories/github-pages-basics
[5]:https://help.github.com/en/articles/further-reading-on-github-pages/
[6]:https://help.github.com/en/categories/customizing-github-pages/
[7]:https://help.github.com/en/articles/about-github-pages-and-jekyll
[8]:https://github.com/jekyll/jekyll
[9]:https://jekyllrb.com/
[10]:https://help.github.com/en/articles/markdown-basics
[11]:https://help.github.com/en/articles/adding-a-jekyll-theme-to-your-github-pages-site-with-the-jekyll-theme-chooser
[12]:https://jekyllrb.com/docs/
[13]:https://jekyllrb.com/docs/installation/macos/
[14]:https://jekyllrb.com/docs/installation/ubuntu/
[15]:https://jekyllrb.com/docs/installation/other-linux/
[16]:https://jekyllrb.com/docs/installation/windows/
[17]:https://msdn.microsoft.com/en-us/commandline/wsl/about
[18]:https://gcc.gnu.org/install/
[19]:https://www.gnu.org/software/make/
[20]:https://pages.github.com/
[21]:https://help.github.com/en/articles/basic-writing-and-formatting-syntax#headings
[22]:https://daringfireball.net/projects/markdown/
[23]:https://www.appinn.com/markdown/
[24]:https://sspai.com/post/45816
[25]:https://help.github.com/en/categories/github-pages-basics
[26]:https://git-scm.com/