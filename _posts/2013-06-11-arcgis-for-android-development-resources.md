---
layout: post
title: "ArcGIS for Android 开发：开发资源"
categories: Tech
tags: [ArcGIS, Android]
comments: true
---

## 文档

从比较实际的角度出发，最有用的是 Esri 的开发帮助文档。

一份是《ArcGIS API for Android 案例教程》，这个时间上比较旧，不过其中用到的 API 没什么变化，开发的过程比较详细，如果有一点 Java 基础，可以轻松入门。下载地址：<http://vdisk.weibo.com/s/Fkr1z> 在线地址：<http://blog.csdn.net/warrenwyf/article/category/784554> 

另一份是《ArcGIS for Android 2.0 开发教程基础版》，时间上相对新一点，对 API 的介绍较多。在线地址：<http://blog.csdn.net/arcgis_mobile/article/category/1161606>

## 网站

### Esri

ArcGIS Runtime SDK for Android 主页：<http://developers.arcgis.com/en/android/>

ArcGIS Runtime SDK for Android 帮助文档：<http://resources.arcgis.com/en/help/android-sdk/concepts/>

ArcGIS Android 10.1.1 API：<http://developers.arcgis.com/en/android/api-reference/> 1.1 版离线下载：<http://vdisk.weibo.com/s/FmsC4>

ArcGIS Runtime SDK for Android 示例代码：<http://developers.arcgis.com/en/android/sample-code/>

ArcGIS Server REST API：<http://resources.arcgis.com/en/help/rest/apiref/>

### 技术博客

ArcGIS_Mobile（已停止更新，并入「ArcGIS产品与技术专栏」）：<http://blog.csdn.net/ArcGIS_Mobile>

ArcgisServer_book：<http://blog.csdn.net/ArcgisServer_book>

ArcGIS产品与技术专栏：<http://blog.csdn.net/arcgis_all>

牛魔王的作坊：<http://blog.csdn.net/warrenwyf>

菩提老王的葡萄架：<http://blog.newnaw.com/>

### 在线教程

Android 官方教程：<https://developer.android.com/training/index.html>

Android 官方教程的中文翻译：<http://wiki.eoe.cn/>

## 可能遇到的问题

* AVD 无法显示本地 AcrGIS Server 地图，查看 DDMS 报「Connection to http://127.0.0.1 refused」：`localhost` 这个地址被 AVD 占用了，把地址改成 `10.0.0.2` 即可。

* Android 真机无法访问电脑上的 ArcGIS Server 本地服务器（查找问题在哪儿可以查看 DDMS）：在 REST 服务地址没错的前提下，原因可能在于 Windows 防火墙阻挡了外部的接入。关闭防火墙即可。

## 书籍

网络的资源用来入门，书上的内容没事翻翻即可。国内的《疯狂 Android 讲义》《Google Android 开发入门与实战》等书不过多推荐，看着也还行。《Learning Android》是我的入门书籍，比较薄，也很全面。英文版下载地址：<http://vdisk.weibo.com/s/FmZ4-> 再加一本《Beginning Android 4》英文版下载地址：<http://vdisk.weibo.com/s/FmX_M>

## 社区

eoe 移动开发者社区：<http://android.eoe.cn/>

Esri 中国社区 Mobile GIS 版：<http://bbs.esrichina-bj.cn/ESRI/forumdisplay.php?fid=27>

Esri 中国社区 ArcGIS Server 技术版：<http://bbs.esrichina-bj.cn/ESRI/forumdisplay.php?fid=25>

华夏土地网 ArcGIS 版：<http://bbs.hxland.com/forum-35-1.html>

## 视频

推荐 Mars 老师的 Android 教程（武大珞樱 PT 上的下载地址，仅限校园网访问）：<http://pt.whu6.edu.cn/details.php?id=320> 也可以追重制版，现在更新到了第二季：<http://www.marschen.com/forum.php?mod=forumdisplay&fid=2>

## 工具

我的建议是用 Google 搜索，技术问题 Google 出来的答案更靠谱。不必害怕英文。对于搜索可能被重置的问题，学会使用 [GoAgent](https://code.google.com/p/goagent/)。