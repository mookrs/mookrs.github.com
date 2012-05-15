---
layout: post
title: "开启Windows「自动播放」功能"
description: ""
category: tech
tags: [windows, skill]
---
{% include JB/setup %}

装好 Windows 后，我通常会禁用“自动播放”这一功能，因为每次插入u盘时弹出的提示都很烦人。这几天 [Dropbox 1.3.13 beta](http://forums.dropbox.com/topic.php?id=53104&replies=849) 版本新增 Import pictures and videos 功能，官方推出活动，试用此功能首次即奖励 500MB 空间，传送更多照片或视频最高可获得 5GB 空间。为了获取空间，我必须开启“自动播放”功能，但是通过打开 控制面板>系统和安全>硬件和声音>自动播放，勾选“为所有媒体和设备使用自动播放(U)”后，插入移动设备并不能自动播放。

于是进一步确定以下两点：

- `Win+R` 打开运行，输入 `services.msc` 并回车，确保 `Shell Hardware Detection` 服务开启 

- 运行 `gpedit.msc`，打开 计算机配置 > 管理模板 > Windows 组件 > 自动播放策略 > 关闭自动播放，双击，勾选 `已禁用(D)`

这样就可以打开“自动播放”功能了。