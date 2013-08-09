---
layout: post
title: "开启 Windows 「自动播放」功能"
category: Tech
tags: [Windows]
comments: yes
---

装好 Windows 后，我通常会禁用「自动播放」这一功能，因为每次插入u盘时弹出的提示都很烦。如果想开启「自动播放」功能，可以通过打开 控制面板>系统和安全>硬件和声音>自动播放，勾选「为所有媒体和设备使用自动播放(U)」。

若这样做无效，则进一步确定以下两点：

- `Win+R` 打开运行，输入 `services.msc` 并回车，确保 `Shell Hardware Detection` 服务开启 

- 运行 `gpedit.msc`，打开 计算机配置 > 管理模板 > Windows 组件 > 自动播放策略 > 关闭自动播放，双击，勾选 `已禁用(D)`