---
layout: post
title: 搭建 GitHub Pages 博客：一、新手入门
---

通过阅读你能了解到：
1. 注册 GitHub 账号；
2. 创建 GitHub 仓库；
3. 通过 GitHub Pages 选择主题；
4. 在线写文章。

——意尽而知其然，思深则所以然。

<!--more-->

# 新手起步
GitHub Pages 是一种静态网站托管服务，内置 Jekyll 渲染工具，不论是 HTML 资源还是 Markdown 文本，都可以渲染为网站。


## 1. 注册 GitHub 账号
GitHub 官方简介：
> The best way to design, build, and ship software.

想要使用 GitHub Pages 服务，首先你得注册一个 GitHub 账号：[注册传送门][1]。

这是 2019 年 06 月的注册页面：

![](/assets/images/github-pages/craete-account.png)

名词释义：
- `Username`：用户名，账号，建议全小写字母，可以使用数字后缀，比如拼音加年份：randall2019。
- `Email address`：邮件地址，建议常用邮箱，一些账户相关的操作会通知到邮箱，保证安全。
- `Password`：密码，口令，建议大小写字母加数字、特殊字符的组合，Chrome 浏览器可以自动生成并保存密码，推荐使用。

点击创建账号按钮，可能会触发机器验证：

![](/assets/images/github-pages/verify-account.png)

通过验证之后，出现两个订阅选项：

![](/assets/images/github-pages/choose-subscription.png)

订阅释义：
- 免费：无限制的开源或私有仓库，最多三人协作的私有仓库，问题和 bug 跟踪系统，工程管理。
- 专业：享受免费订阅所有功能，包括无限协作的私有仓库，以及高级工具和高级洞察系统。

这里我们选择免费订阅，然后继续：

![](/assets/images/github-pages/continue-account.png)

选项释义：
- `Help me set up an organization next`：帮助建立组织，这个对于个人来说，没有勾选的必要。
- `Send me updates on GitHub news, offers, and events`：发送最新的 GitHub 新闻、优惠、活动，跟随默认呢就好。

点击继续按钮，出来一堆选项：

![](/assets/images/github-pages/tailor-experience.png)

选项释义：
- `What is your level of programming experience?`：询问编程水平。按从上到下的顺序，分别是：
  - 无
  - 新手
  - 熟练
  - 精通
- `What do you plan to use GitHub for? (Select up to 3)`：询问使用方式，最多选三个答案。按从上到下的顺序，分别是：
  - 学习代码
  - 学习 Git 和 GitHub
  - 托管项目（仓库）
  - 用 GitHub Pages 创建网站
  - 团队合作
  - 寻找合适项目
  - 学校工作和项目
  - GitHub API
  - 不知道
  - 其他（请注明）
- `What are you interested in?`：询问兴趣爱好，需要用英文填写。

一般来说，我们只需要点击旁边那个 `skip this step` 按钮，当然，你也可以选择填写这份问卷调查，反正闲着也是闲着。

提示验证邮箱地址：

![](/assets/images/github-pages/hint-verify-email.png)

注意，如果填错邮箱，这没关系，我们到账户设置中添加新邮箱：

![](/assets/images/github-pages/add-email.png)

随后到邮箱中查收邮件并进行验证，再检查账户状态：

![](/assets/images/github-pages/finish-account.png)

至此，完成账号的注册。


## 2. 创建 GitHub 仓库
仓库是项目的存储库，依托于 Git 工具的强大，项目可以很好地保存在 GitHub 上，即使服务在未来不可用，只要你本地拥有项目副本，那么通过 Git 命令可以将项目转移到 [Gitee][2] 上。

先放下关于 Git 的诸多疑问，咱们来创建一个全新的仓库：

![](/assets/images/github-pages/new-repositories.png)

通常我们命名为 `<username>.github.io`，这是作为博客仓库使用：

![](/assets/images/github-pages/create-blog.png)

名词释义：
- `Owner`：所有者，就是你的账号。
- `Repository name`：仓库名字，必填，不能与已有的仓库重名，因此建议按一定的规律命名。
- `Description`：简介，可选项，一般用一句话描述仓库的作用。
- `Public/Private`：开源或私有，开源则所有人可见，私有则只有自己和协作者可见。
- `Initialize this repository with a README`：初始化仓库的自述文件，默认勾选就好。
- `Add .gitignore`：添加 Git 忽略策略，一般不是开发者不需要关心这里，它是用来排除某些文件夹和文件，不计入版本管理。
- `Add a license`：添加许可声明，不需要在创建之初就添加，通常用来声明使用某种开源许可。

*提示：需要创建以其他方式命名的仓库，请跳过之后的内容，参考 [【搭建 GitHub Pages 博客】二、进阶知识][3] 即可。*

填写完毕后，点击创建仓库按钮，至此完成仓库的创建。


## 3. 通过 GitHub Pages 选择主题
选择主题并非本文的核心，所以你也可以**跳过这一节的内容**。

找到仓库设置：

![](/assets/images/github-pages/find-setting.png)

在 GitHub Pages 设置中，点击选择主题按钮：

![](/assets/images/github-pages/find-choose-theme.png)

随便选一个主题，这里我选的是 [cayman][4]：

![](/assets/images/github-pages/choose-the-theme.png)

系统自动创建并更新了 README.md 文件：

![](/assets/images/github-pages/set-theme-cayman.png)

直接提交改动：

![](/assets/images/github-pages/update-readme-for-theme-change.png)

过一会儿，打开 `<username>.github.io`，可以看到网站首页：

![](/assets/images/github-pages/my-first-blog.png)

主题对于网站的帮助是巨大的，否则你看到的将只是一段段简单的纯文本，甚至它们可能像 txt 一样难以驾驭。


## 4. 在线写文章
这个网站首页由 Jekyll 读取 `README.md` 文件渲染生成，对于 Markdown 文件的疑惑先放到一边，我们来试试在线写文章。

点击 `Create new file` 按钮创建一个文件：

![](/assets/images/github-pages/create-new-file.png)

将文件命名为 `*.md` 格式，随便写上一句话：

![](/assets/images/github-pages/input-first-post.png)

提交到仓库：

![](/assets/images/github-pages/commit-first-post.png)

在浏览器中打开 `<username>.github.io/001.天气不错`，查看内容：

![](/assets/images/github-pages/preview-first-post.png)

至此，大功告成！


# 总结
GitHub 提供的 GitHub Pages 服务非常方便，仅仅在浏览器中就可以创建和更新自己的博客，真是太棒了！

不过官方主题还是有些空洞，而我希望我的博客有不同风格以及子分类，那么我就需要了解更多的知识来自定义它。



[1]:https://github.com/join?source=header-home
[2]:https://gitee.com/
[3]:/2019/06/07/github-pages-advanced-knowledge/
[4]:https://github.com/pages-themes/cayman