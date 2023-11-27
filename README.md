mrzhqiang 的个人博客
===================

这是程序员博客的源码仓库，基于 Bootstrap4 框架构建，使用 Jekyll 工具渲染网页，托管在 GitHub Pages 服务上。

---

## 在线浏览

传送门：[mrzhqiang.github.io][1]。

## 本地开发

- 必备环境：[Jekyll Requirements][2]
- 开发环境：
  - [Windows][3]
  - [macOS][4]
  - [Ubuntu][5]
  - [Other Linux][6]

注意，对于 `gem update`，需要安装依赖：

```bash
sudo apt-get install ruby-dev
```

为了加速下载依赖，可以替换国内 Gem 源（可选）：

```bash
gem sources -add https://gems.ruby-china.com --remove https://rubygems.org/

gem sources -l
```

最后，运行本地服务器：

  ```bash
  $ bundle exec jekyll serve
  ```

如果还有其他问题，请参考：[Jekyll Docs][0]。



[1]:https://mrzhqiang.github.io/
[2]:https://jekyllrb.com/docs/installation/#requirements
[3]:https://jekyllrb.com/docs/installation/windows/
[4]:https://jekyllrb.com/docs/installation/macos/
[5]:https://jekyllrb.com/docs/installation/ubuntu/
[6]:https://jekyllrb.com/docs/installation/other-linux

[0]:https://jekyllrb.com/docs
