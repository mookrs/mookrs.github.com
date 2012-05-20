---
layout: post
title: "解决「The realtek network controller was not found」"
description: ""
category: tech
tags: [realtek, windows, 驱动, skill]
---
{% include JB/setup %}

家里今天配了一台电脑，主板是昂达 N68GD3，Win7 32 位下有线网卡不能直接驱动。当时没有其它电脑在手边，还好试着挂载了一下 Ubuntu 镜像，能连上网络。根据 [ZOL](http://detail.zol.com.cn/motherboard/index294964.shtml) 的硬件信息找到 Realtek RTL8103E 的相关驱动，安装报错“FindFile failed”，然后继续报错“The Realtek Network Controller was not found.IF Deep Sleep Mode is enabled Please Plug the Cable.”意思是 Realtek 网络控制器未找到，如果进入了深度睡眠状态，请插上网线。

搜索到[国外的一个网站](http://adeelejaz.com/blog/realteks-network-controller-deep-sleep-mode-issue/)是这样解答的：大意是要先关机，开机箱取出 CMOS 电池和内存条，等到主板、内存都处于掉电状态，相关信息自动重置后，再放入 CMOS 电池并插上内存条。但是我考虑电脑在 Ubuntu 下是可以联网的，应该不是网卡的问题也用不着拆机箱，再说也没法拆。

我再去别的网站找网卡驱动，这次没有报错“FindFile failed”，不过还是报“The Realtek Network Controller was not found.IF Deep Sleep Mode is enabled Please Plug the Cable.”这时找到[一个豆友的文章](http://www.douban.com/note/189617233/)，去了下 [Realtek 的官网](http://www.realtek.com.tw/)，到[这个页面](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=3&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)下载了驱动文件 Win7 and WinServer 2008 R2 Auto Installation Program (SID:1483418)，安装后网卡在设备管理器里即可识别。

问题在于没下对驱动，所以还是装官网上的驱动最好。