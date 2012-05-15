---
layout: post
title: "Hello Jekyll"
description: ""
category: tech
tags: [jekyll, skill]
---
{% include JB/setup %}

这是我迁移到 [Jekyll](https://github.com/mojombo/jekyll) 后的第一篇文章。Jekyll 是个很好的博客系统，可以部署到免费的 [Heroku](http://www.heroku.com/) 或 [Github Page](http://pages.github.com/) 上，也可以部署到自己的服务器伤。之前在 Windows 和 Ubuntu 环境下尝试配置了 [Octopress](http://octopress.org/)，但总有小毛病，于是转向 Jekyll（其实是用了 [Jekyll-Bootstrap](http://jekyllbootstrap.com/)）。我没有接触过 Ruby，也不懂得 git 原理，所以其中的过程可谓历尽波折，编码就困扰过我一个通宵……However, it works now!

以下是部署 Jekyll 或 Octopress 的参考链接：

[在 Windows7 下从头开始安装部署 Octopress](http://sinosmond.github.com/blog/2012/03/12/install-and-deploy-octopress-to-github-on-windows7-from-scratch/)

[Github Pages极简教程](http://chen.yanping.me/cn/blog/2012/03/18/github-pages-step-by-step/)

[使用Github Pages建独立博客](http://beiyuu.com/github-pages/)

[Octopress搭建Blog：配置篇](http://evsseny.appspot.com/2012/03/30/Octopress-blog-Configuration.html)

学习Git的参考链接：

[git - 简易指南](http://rogerdudler.github.com/git-guide/index.zh.html)（适合初学者的概览）

[GotGitHub](http://www.worldhello.net/gotgithub/index.html)

[Git Community Book 中文版](http://gitbook.liuhui998.com/index.html)

在Windows上搭建Ruby on Rails环境，强烈建议使用[RailsInstaller](http://railsinstaller.org/)，它包含了[Ruby](http://ruby-lang.org/) 、[Rails](http://rubyonrails.org/)、 [Bundler](http://gembundler.com/)、 [Git](http://git-scm.com/)、[Sqlite](http://sqlite.org/)、 [TinyTDS](https://github.com/rails-sqlserver/tiny_tds)、 [SQL Server support](https://github.com/rails-sqlserver/activerecord-sqlserver-adapter)和[DevKit](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit)。我换了个git的版本。

一些需要记录的：

####设置gem的更新源

`gem sources --remove http://rubygems.org/`

`gem sources -a http://ruby.taobao.org/`

`gem sources -l`

确保只有`http://ruby.taobao.org`输出

####测试git是否连接正常

`ssh -T git@github.com`

####安装用来解析markdown语言的rdiscount或kramdown

`gem install rdiscount kramdown`

####配置_config.yml文件

_config.yml里的的冒号后必须要有空格，否则会报错。如果有中文，需要存成UTF-8格式。修改固定链接格式为'/:year/:month/:title.html'，其它选项有必要的都一一修改好。

####Windows下文章或标题有中文则不能生成网站

参考这里：[http://www.oschina.net/question/129471_37163](http://www.oschina.net/question/129471_37163)

编辑

`D:\RailsInstaller\Ruby1.9.3\lib\ruby\gems\1.9.1\gems\jekyll-0.11.2\lib\jekyll\convertible.rb`

第27行

`self.content = File.read(File.join(base, name))`

替换为

`self.content = File.read(File.join(base, name), :encoding => "utf-8")`

####其它

添加CNAME，404页面。

将Disqus改成国内的多说或者友言是没问题的，不过考虑到博客的受众，我决定保留Disqus。