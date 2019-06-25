---
layout: post
title: 搭建 GitHub Pages 博客——2. 进阶知识
---

学习使用 GitHub Pages 搭建拥有自己风格的博客站点。

- [x] 基础入门：GitHub。

- [x] 进阶知识：GitHub Pages、Jekyll。

- [ ] 融会贯通：Git、Markdown、Bootstrap。

<!--more-->

## 进阶知识
建立了一个基于官方主题的博客，可是样式还不够精致，我需要动手改造一下。

### GitHub Pages
首先从仓库的设置页面里看到，它是基于 GitHub Pages 服务。

![](/assets/images/github-pages/pages-learn-more.png)

点击 [学习更多][1] 按钮，了解到以下要点：

- 博客可以在 `master` 分支下发布，也可以通过 `gh-pages` 分支发布，或者在 `master` 分支下的 `/docs` 文件夹中发布。
- 如果仓库名是 `<username>.github.io` 的话，只能从 `master` 分支发布。

*建议：使用 `<username>.github.io` 作为博客仓库，`gh-pages` 和 `/docs` 作为项目文档，其中 `/docs` 更适合小项目。*

这里发现 [什么是 GitHub Pages][2] 链接，点进去看看：

> GitHub Pages is a static site hosting service designed to host your personal, organization, or project pages directly from a GitHub repository.

简单来说，GitHub Pages 就是存储在云端并让其他人可以访问我们网站的服务。

关于 GitHub Pages 的使用限制如下：

- 源仓库大小建议限制为 1GB，包括作为静态网站的文件。
- 网站的每月访问流量被限制为 100GB，这是一个软带宽限制。
- 每小时提交到 GitHub Pages 的版本限制为 10 个，这也是一个软限制。

*软限制：可能就是弹性限制，允许有左右浮动；或者是未来会进行调整的限制。*

如果有兴趣了解更多，请参考：[GitHub Pages 基础知识][3]。


### Jekyll
我在 [GitHub Pages 进阶知识][44] 中，找到 [自定义 GitHub Pages][5] 链接，这就是我需要的东西。

对于 Jekyll，[关于 GitHub Pages 和 Jekyll][6] 这篇文章描述得很清楚：

> GitHub Pages is deeply integrated with Jekyll, a popular static site generator designed for blogging and software documentation, but used for much more.

这是 [Jekyll 源码仓库][7]，它的文档在这里：[Jekyll 文档][8]。

按照文档操作，一切将变得非常轻松。


## 总结
GitHub Pages 托管你的博客站点，Jekyll 设计你的博客主题，一切都好像挺完美的。

[1]:https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages
[2]:https://help.github.com/en/articles/what-is-github-pages
[3]:https://help.github.com/en/categories/github-pages-basics
[4]:https://help.github.com/en/articles/further-reading-on-github-pages/
[5]:https://help.github.com/en/categories/customizing-github-pages/
[6]:https://help.github.com/en/articles/about-github-pages-and-jekyll
[7]:https://github.com/jekyll/jekyll
[8]:https://jekyllrb.com/