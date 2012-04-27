---
layout: post
title: "HP Pavilion g4-1208tx笔记本PE下不识别硬盘"
description: ""
category: tech
tags: [ide, pe, sata, skill]
---
{% include JB/setup %}

同学的弟弟买了一款[HP Pavilion g4-1208tx](http://www.360buy.com/product/533472.html)笔记本，预装Windows 7 Home Basic 64bit系统，惠普的还原软件占用了10多G，结果卖电脑的JS死活不给删除这个分区，要是删除重新分区就得买杀毒软件，我说得了我给你装系统。于是我按照常规步骤打算用深度Windows PE硬盘安装系统。进入PE发现750G的硬盘连根毛都没看着……只能看见我自己的U盘……

经过搜索应该在BIOS里把硬盘模式改成IDE，但是惠普的BIOS里根本没有IDE模式开关。因此得改用带SATA驱动的PE，试了几个以后还是没法识别。干脆直接用[Win7内核的PE](https://www.google.com/search?hl=zh-cn&q=Win7%E5%86%85%E6%A0%B8%E7%9A%84PE)，进入PE以后果然可以识别硬盘了。正常分区，装系统和软件，完成。装系统的同时我还顺便在帮刷HTC A510c的系统……本来美好的周末累死了……