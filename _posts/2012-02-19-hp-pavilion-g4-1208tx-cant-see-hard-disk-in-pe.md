---
layout: post
title: "HP Pavilion g4-1208tx笔记本PE下不识别硬盘"
description: ""
category: tech
tags: [windows, hard disk, skill]
---
{% include JB/setup %}

同学的弟弟买了一款 [HP Pavilion g4-1208tx](http://www.360buy.com/product/533472.html) 笔记本，预装 Windows 7 Home Basic 64bit 系统，惠普的还原软件占用了10多G，结果卖电脑的 JS 死活不给删除这个分区，要是删除重新分区就得买杀毒软件，我说得了我给你装系统。于是我按照常规步骤打算用深度 Windows PE 硬盘安装系统。进入 PE 发现 750G 的硬盘连根毛都没看着……只能看见我自己的U盘……

经过搜索应该在 BIOS 里把硬盘模式改成 IDE，但是惠普的 BIOS 里根本没有 IDE 模式开关。因此得改用带 SATA 驱动的 PE，试了几个以后还是没法识别。干脆直接用 [Win7 内核的 PE](https://www.google.com/search?hl=zh-cn&q=Win7%E5%86%85%E6%A0%B8%E7%9A%84PE)，进入 PE 以后果然可以识别硬盘了。正常分区，装系统和软件，完成。装系统的同时我还顺便在帮刷 HTC A510c 的系统……本来美好的周末累死了……