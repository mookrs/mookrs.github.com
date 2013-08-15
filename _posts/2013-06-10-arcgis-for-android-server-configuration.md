---
layout: post
title: "ArcGIS for Android 开发：ArcGIS for Server 配置"
categories: Tech
tags: [ArcGIS, Android]
comments: true
---

对于 Server 的安装以及配置，在《ArcGIS 10.1 for Server 入门教程》这份文档中有详细的说明，文档下载地址（你需要一个新浪微博账号登陆下载）：<http://vdisk.weibo.com/s/FeDrG>

### 安装

[ArcGIS 10.1 for Server 下载地址](http://pan.baidu.com/share/link?shareid=1622335099&uk=1731248969)

安装参考文档「2.2 Windows 系统下的安装」 。

其中有一步需要创建 Server 账户和密码。该账户会在你的 Windows 系统中存在，跟 ArcGIS Server 有关的进程都会在此账户下运行。

### 授权

这部分请自行搜索方法。

**注意：要想能够登陆 Manager，必须确保在任务管理器中 ArcGISServer.exe 进程正在运行。如果没有运行，到任务管理器的服务选项卡中启动。安装 ArcGIS for Server 后该服务会开机运行，很占内存，可以考虑在服务管理中将「启动类型」改为「手动」：**

![](/static/img/2013/06/Service.png) 

### 配置

参考文档「2.3 配置（单机部署）」。

### 发布 Map Service

参考文档「3.2 在 ArcCatalog 中发布 Map Service」。

我们借助 REST 服务操作地图，地图服务启用的每个功能都对应一个 URL。

比如我们的地图服务命名为 WhuMap，保存在 root 根目录下，那么 REST 服务的访问地址则形如 <http://localhost:6080/arcgis/rest/services/WhuMap/MapServer>，这也是在 Java 代码中 ArcGISDynamicMapServiceLayer 所使用的地址。如果用 AVD 开发，要把 `localhost` 改为 `10.0.0.2`；如果用真机开发，要把真机和运行着 ArcGIS for Server 的电脑置于同一个局域网内，在 PC 的 cmd 窗口中输入 `ipconfig`，获得本机的 IP 地址，例如用 `192.168.43.219` 替代 `localhost`。