MRZHQIANG PERSONAL BLOG
=======================

[![Build Status](https://travis-ci.org/mrzhqiang/mrzhqiang.github.io.svg?branch=master)](https://travis-ci.org/mrzhqiang/mrzhqiang.github.io)

A simple, static portal which personal blogs, resource favorites, and some interesting things.

Well, it looks a lot like [okhttp](https://github.com/square/okhttp) because it's copied from [okhttp](https://github.com/square/okhttp).


Development
-----------
### Prerequisite
- clone or pull the repository's lastest code at master branch
```bash
git clone git@github.com:mrzhqiang/mrzhqiang.github.io.git
```
- see about [Jekyll docs](https://jekyllrb.com/docs)


### Run the site locally
```bash
gem install bundler # first time only
bundle install # first time only
bundle exec jekyll serve
```


### Update list of repos:
```bash
pip install pystache requests pygithub3 # first time only
./generate.py
```
