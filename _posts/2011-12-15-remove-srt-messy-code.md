---
layout: post
title: "消除BIG5编码造成的字幕乱码"
category: tech
tags: [encoding, skill]
---

最近在读三岛由纪夫的《[春雪](http://book.douban.com/subject/3987362/ "豆瓣链接")》，刚好下载到改编自这本书的[同名电影](http://movie.douban.com/subject/1478789/ "豆瓣链接")，打算观看却发现外挂字幕显示乱码。原因在于字幕采用了繁体中文编码 BIG5，而我的 PotPlayer 播放器在字幕选项里编码设定的是简体中文编码 GB2312。为了不影响播放器正常播放简体中文字幕，采用下面的简单方法对字幕进行调整。

![](http://farm8.staticflickr.com/7086/7112438069_25958720b1.jpg)

1\.将乱码的 srt 格式字幕的后缀改为 txt，编码以 ANSI 保存而不是 Unicode。

2\.用浏览器打开这个 txt 文件。当然，还是乱码一片。

![](http://farm8.staticflickr.com/7185/6966361144_54be7b6f5e.jpg)

3\.将编码改为繁体中文（Big5）。

![](http://farm8.staticflickr.com/7139/7112437795_bbc263acf5.jpg)

原本内容为繁体的字幕这时被正确显示。

![](http://farm8.staticflickr.com/7048/6966360870_a3a4520c48_z.jpg)

4\.把调整好的内容 ctrl+a 全部复制下来，覆盖到 txt 文件中，再将 txt 格式改回 srt。

效果测试如下：

![](http://farm8.staticflickr.com/7092/6966360684_f324aeacba.jpg)