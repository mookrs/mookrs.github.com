---
layout: post
title: "ArcGIS Desktop 10 图文安装教程"
description: ""
category: tech
tags: [arcgis, software]
---
{% include JB/setup %}

地理信息系统相关专业的同学一定少不了要用到 ArcGIS。之前有同学要我帮忙装这个软件，我想既然“授人以鱼不如授人以渔”，那我来结合网上的文章写一个教程好啦。

#### 1.下载 ArcGIS Desktop 10

(1) [官方地址](http://software.esri.com/akdlm/software/arcgis/10.0/final/ArcGIS_Desktop10_122519.iso?downloadID=FA0A478D-1C44-4915-83E1-4BC130EBFF48&__gda__=1283497777_a635b797d7b418fd134cf372fc88e67e&ext=.iso&__gdb__=1283497778_cc0ecad33f057a2fbbe5b79fc5d77825&fileExt=.iso)  [eMule 地址](ed2k://|file|ArcGIS_Desktop10_122519.iso|4031676416|B77214643D9068A51826E4B77365B4C7|h=ABDJVPGGZJEMVNIA24SBT42D2B7C3HJS|/)

复制链接，在迅雷等下载软件里新建任务即可。注意，这个 3.75G 的 ArcGIS_Desktop10_122519.iso 文件为英文版，不包含补丁。

(2) [sp2补丁地址](http://resources.arcgis.com/zh-cn/content/patches-and-service-packs?fa=viewPatch&PID=15&MetaID=1752)  [sp3补丁地址](http://resources.arcgis.com/zh-cn/content/patches-and-service-packs?fa=viewPatch&PID=15&MetaID=1807)

目前 ArcGIS Desktop 10 的版本已更新到 Service Pack 3（2011-10-12）。但因为我手头没有这个补丁，下载又比较费时间，这里以 sp2 演示。升级到 sp2 并不需要先升级到 sp1，可以直接安装 sp2 补丁。由于我们仅安装 Desktop 和 LicenseManager，所以只需下载 ArcGISDesktop10sp2.msp 和 ArcGISLicenseManager10sp2.msp 这两个补丁文件。如图：
![](http://farm8.staticflickr.com/7036/7112394987_baa93b3916_z.jpg)

(3) 注册机 [115地址](http://115.com/file/dn3p6nh8#) [Box地址](http://www.box.com/s/elb10n41962jmbujrm0v)

请务必保证非商业使用，仅供个人学习和研究，如需要请购买正版！

#### 2.安装 ArcGIS Desktop 10

(1) 使用 [DAEMON Tools Lite](http://www.xngq.com/products/dtLite) 一类软件加载 iso 镜像文件，运行安装包里的 ESRI.exe，选择安装 ArcGIS Desktop。先安装 Desktop 或者 License Manager 都可以。

![](http://farm9.staticflickr.com/8007/6966317916_c0ded6745a_z.jpg)

ArcGIS Desktop 10 需要 .NET Framwork 3.5 SP1 支持，如果系统中没有安装时会提示。安装包中已附带 .NET Framwork 3.5 SP1。

![](http://farm8.staticflickr.com/7240/7112394707_569b98c6c1_z.jpg)

安装全过程看图说话：

![](http://farm8.staticflickr.com/7125/6966317674_30d34d9f67_z.jpg)

![](http://farm6.staticflickr.com/5463/7112394517_39d2f8c131_z.jpg)

![](http://farm6.staticflickr.com/5442/7112394415_517964e0fb_z.jpg)

![](http://farm9.staticflickr.com/8007/6966316890_32cc38d472_z.jpg)

![](http://farm8.staticflickr.com/7109/7112394005_759ac56f22_z.jpg)

![](http://farm8.staticflickr.com/7051/6966316786_dc35a49398_z.jpg)

Desktop 安装完出现 ArcGIS Administrator Wizard，如图，第2项填 localhost，也可以在后面配置：

![](http://farm8.staticflickr.com/7248/7112393523_f563a365da_z.jpg)

![](http://farm8.staticflickr.com/7062/6966317178_5167ac4a4c_z.jpg)

(2) 回到主界面，安装 ArcGIS License Manager

![](http://farm8.staticflickr.com/7069/6966317336_1fac231855_z.jpg)

一路 next 就好了哇……

![](http://farm6.staticflickr.com/5441/6966316108_68ec96bb76_z.jpg)

(3) 安装 sp2 补丁

分别运行 ArcGISDesktop10sp2.msp 和 ArcGISLicenseManager10sp2.msp，点 next 后补丁会自动更新软件。

![](http://farm8.staticflickr.com/7109/7112392903_0506de48ae_z.jpg)

#### 3.进行授权

(1) 打开注册机，Feature 选择 ARC/INFO，点击 All，会生成授权文件内容

![](http://farm8.staticflickr.com/7244/7115473181_507cfe85de_z.jpg)

复制生成的内容到到 License Manager 的安装目录（默认为：C:\ProgramFiles\ArcGIS\License10.0\bin\）下，替换 service.txt 里的内容即可。

补充说明：想授权几个功能就选择相应的功能按添加（Add），按移除（Remove）可以移除上一个授权，按清除（Clear）可清除所有已添加的授权，授权所有功能按所有（All）即可。

(2) 通过开始菜单，打开 License Server Administrator，查看服务是否已经启动，如果没有启动，先启动服务。

![](http://farm8.staticflickr.com/7185/6966316422_0f8ae60ca1_z.jpg)

许可服务器状态：正在运行

![](http://farm8.staticflickr.com/7063/7112393409_40686b0fb8_z.jpg)

然后打开 ArcGIS Administrator，选择 ArcInfo（浮动使用），输入许可管理器计算机名（如果之前已经输入过，那么这一步可忽略）。

![](http://farm8.staticflickr.com/7120/7112393209_3d1a54b62f_z.jpg)

好了，大功告成！ArcGIS Desktop 10 完成了安装和授权，现在可以正常使用了。

![](http://farm8.staticflickr.com/7179/6966316220_bbd3ae28ef_z.jpg)

为了写这篇文章我把早装好的 ArcGIS 卸载了……真是……胃疼啊……截了这么多图应该没有让人不明白的地方了吧……

另外安装的时候可能会出现某些比较奇怪的问题，这些奇奇怪怪的问题大部分是由于系统精简和清理过度造成的，不在讨论范围内……这个，我从来是建议重装系统的……