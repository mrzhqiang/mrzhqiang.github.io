mrzhqiang 的个人博客
===================
这是一枚小程序员的博客源码仓库。

## 在线浏览
传送门：[Web](https://mrzhqiang.github.io/)。

## 本地预览
首先确保拥有以下环境：

- ruby 2.4.0 或者更高：`ruby -v`
- gem 环境：`gem -v`
- GCC 和 Make 环境：`gcc -v`, `g++ -v` 以及 `make -v`

接着 clone 本仓库的 master 分支，进入仓库根目录，执行以下命令：

```bash
$ gem install bundler # first time only
$ bundle install # first time only
$ bundle exec jekyll serve
```

**注意：如果提示权限问题，请使用 sudo 作为 root 用户执行上面的命令。**

**提示：如果出现下面的问题，请参考：https://blog.csdn.net/ls1160/article/details/38170463。**
```bash
An error occurred while installing nokogiri (1.10.3), and Bundler cannot continue.
Make sure that `gem install nokogiri -v '1.10.3' --source 'https://rubygems.org/'` succeeds before bundling.
```

如果还有其他问题，请参考：[Jekyll Docs][1]。

写在最后
-----------
作为程序员，要始终记得，遇到问题不用害怕，就怕遇不到问题！！



[1]:https://jekyllrb.com/docs
