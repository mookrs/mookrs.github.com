---
layout: post
title: "ArcGIS Runtime SDK for WPF 环境下 PictureMarkerSymbol 向右下方偏移"
categories: tech
tags: [ArcGIS, WPF, PictureMarkerSymbol]
comments: yes
---

做基于 ArcGIS Runtime SDK for WPF 的地图开发时，我希望利用 PictureMarkerSymbol 在地图上放置一个定位图片，标识出查询得到的地点。但是发现总有偏移，如图：

![](/static/img/2013/11/PictureMarkerSymbol-1.jpg)

这种情况下，一旦缩小地图，偏移量就会特别厉害：

![](/static/img/2013/11/PictureMarkerSymbol-2.jpg)

原因我猜测是由于图片默认以左上方的顶点定位，所以虽然左上方确实在中心位置，但是整张图片的看起来已经偏移了。

解决办法是，为 PictureMarkerSymbol 的 OffsetX 和 OffsetY 属性设置为图片宽度和长度一半的值，例如 `OffsetX="15" OffsetY="25"` 即可：

![](/static/img/2013/11/PictureMarkerSymbol-3.jpg)

参考链接：<http://forums.arcgis.com/threads/96639-PictureMarkerSymbol-Shifting-on-Zoom>