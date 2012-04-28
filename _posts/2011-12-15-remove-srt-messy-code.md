---
layout: post
title: "消除SRT字幕乱码的一个办法"
description: ""
category: tech
tags: [编码, 字幕, skill]
---
{% include JB/setup %}

最近读三岛由纪夫的《[春雪](http://book.douban.com/subject/3987362/ "豆瓣链接")》，非常喜欢。刚好下载到改编自这本书的[同名电影](http://movie.douban.com/subject/1478789/ "豆瓣链接")，打算观看却发现外挂字幕显示乱码。查了一下这个是简体中文中文编码GB2312和繁体中文编码BIG5的不一致的问题。

![](http://farm8.staticflickr.com/7086/7112438069_25958720b1.jpg)

于是用比较简单的方法对字幕进行如下调整。

1\.将乱码的srt格式字幕的后缀改为txt。

2\.用浏览器（IE/Chrome/Firefox/Safari/Opera）打开这个txt文件。当然，还是乱码一片。

![](http://farm8.staticflickr.com/7185/6966361144_54be7b6f5e.jpg)

3\.将编码改为繁体中文(Big5)。

![](http://farm8.staticflickr.com/7139/7112437795_bbc263acf5.jpg)

原本内容为繁体的字幕这时被正确显示。

![](http://farm8.staticflickr.com/7048/6966360870_a3a4520c48_z.jpg)

4\.把调整好的内容ctrl+a全部复制下来，覆盖到txt文件中，再将txt格式改为srt。

效果测试如下~

![](http://farm8.staticflickr.com/7092/6966360684_f324aeacba.jpg)