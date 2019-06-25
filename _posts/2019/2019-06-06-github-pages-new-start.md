---
layout: post
title: 【搭建 GitHub Pages 博客】一、新手起步
---

本文是搭建 GitHub Pages 博客三步骤的第一步，通过阅读你能了解到：

1. 创建 GitHub 账号；
2. 创建 GitHub Pages 仓库；
3. 选择博客主题；
4. 在线编写博客文章。

——意尽而知其然，思深则所以然。

<!--more-->

# 新手起步
GitHub Pages 是一种静态网站托管服务，内置 Jekyll 渲染工具，不论是 HTML 资源还是 Markdown 文本，都可以渲染为网站。


## 一、创建 GitHub 账号
GitHub 官方简介：
> The best way to design, build, and ship software.

想要使用 GitHub Pages 服务，首先你得创建一个 GitHub 账号：[注册传送门][1]。

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

随后到邮箱中查收邮件并进行验证，至此你完成了创建账号的所有步骤：

![](/assets/images/github-pages/finish-account.png)


## 二、创建 GitHub Pages 仓库
仓库是对项目的有效管理，依托于 Git 工具的强大，你的项目可以很好地保存在 GitHub 上。

先放下诸多疑问，咱们来创建一个全新的仓库：

![](/assets/images/github-pages/new-repositories.png)

- 2.2 通常我们将仓库命名为 `username.github.io`，这是作为博客仓库使用。

![](/assets/images/github-pages/create-blog.png)

*提示：如果需要其他命名方式，那么这一节可能不适合你阅读。*

### 步骤三：选择主题（可选）
- 3.1 要为博客选择一个主题，请先找到仓库的设置选项。

![](/assets/images/github-pages/find-setting.png)

- 3.2 随后找到设置中的 GitHub Pages 项目，点击选择主题按钮。

![](/assets/images/github-pages/find-choose-theme.png)

- 3.3 这里第一个就很好看，那就是它了。

![](/assets/images/github-pages/choose-the-theme.png)

- 3.4 主题被替换后，README.md 文件自动更新。

![](/assets/images/github-pages/set-theme-cayman.png)

- 3.5 我们提交这一次的更新。

![](/assets/images/github-pages/update-readme-for-theme-change.png)

- 3.6 过一小会儿，可以从 `username.github.io` 上面看到我们的博客。

![](/assets/images/github-pages/my-first-blog.png)

### 步骤四：写文章
现在，我们忽略所有的规则，从最简单的地方开始写文章。

- 4.1 创建一个新的文件。

![](/assets/images/github-pages/create-new-file.png)

- 4.2 文件作为 `.md` 格式，随意写入内容。

![](/assets/images/github-pages/input-first-post.png)

- 4.3 提交这个新文件到仓库。

![](/assets/images/github-pages/commit-first-post.png)

- 4.4 在浏览器中输入 `username.github.io/001.天气不错` 查看第一篇文章。

![](/assets/images/github-pages/preview-first-post.png)

大功告成！

# 总结
从现在开始，我们可以在 GitHub 上写博客，而且步骤非常简单。



[1]:https://github.com/join?source=header-home