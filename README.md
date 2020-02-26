# mrzhqiang 的个人博客

这是一枚小程序员的博客源码仓库。


## 在线浏览

传送门：[mrzhqiang.github.io][1]。

## 本地预览
- 开发环境：[requirements][2]
  - [Windows][3]
  - [macOS][4]
  - [Ubuntu Linux][5]
  - [Other Linux distros][6]
  
- 关于 `gem update`，需要以下依赖：
  ```bash
  sudo apt-get install ruby-dev
  ```

- 替换国内 Gem 源（可选操作）：

  ```bash
  gem sources -add https://gems.ruby-china.com --remove https://rubygems.org/
  
  gem sources -l
  ```

- 运行本地服务器：

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
