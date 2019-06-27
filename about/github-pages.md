---
layout: about
title: 关于 GitHub Pages
---


# {{ page.title }}
官方简介：
> GitHub Pages is a static site hosting service designed to host your personal, organization, or project pages directly from a GitHub repository.

文档传送门：[GitHub Pages Basics][1]

**个人总结：最省心的博客托管服务。**

## 一、简单步骤
1. [注册账号][2]：比如 `<username>`。
2. [创建仓库][3]：比如 `<username>.github.io` 或者 `<any repository name>`。
3. 选择主题（非必要步骤）：`https://github.com/<username>/<username>.github.io/settings/pages/themes?select=cayman&source=master`。
4. 确定来源：默认使用 `master` 分支，可以选 `master` 分支下的 `/docs` 文件夹，以及 `gh-pages` 分支作为发布站点源文件。

**提示：【选择主题】和【确定分支】，在当前项目的 `Settings` 中可以找到并进行修改。**

## 二、核心要点

1. 每个账号有且仅有一个 `<username>.github.io` 仓库，官方推荐作为用户页面站点。
2. 用户页面站点只能从 `master` 分支发布，并且仓库本身就是站点源。
3. 组织页面站点是 `<orgname>.github.io` 仓库，发布限制与用户页面站点相同。
4. 其他仓库想建立文档，则源文件可以在 `gh-pages` 分支下，也可以放进 `master` 分支的 `/docs` 文件夹中。
5. `gh-pages` 分支下不能有“杂质”，也就是说，它只能包含站点源。
6. 即使是私有仓库，一旦选择发布 GitHub Pages 站点，则始终可公开访问。
7. 通过域名映射，将 `<username.github.io>` 改为你自己的域名。
8. 站点源除常规 HTML 文件外，还支持 Jekyll 这个静态站点生成器。

## 三、Jekyll
GitHub 介绍：[About GitHub Pages and Jekyll][4]。

官方文档：[Jekyll][5]。

个人总结：[About Jekyll][6]



[1]:https://help.github.com/en/categories/github-pages-basics
[2]:https://github.com/join?source=header-home
[3]:https://github.com/new
[4]:https://help.github.com/en/articles/about-github-pages-and-jekyll
[5]:https://jekyllrb.com
[6]:/about/jekyll