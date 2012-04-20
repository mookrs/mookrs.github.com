---
layout: post
title: "Ubuntu使用过程中的几个小问题"
description: ""
category: tech
tags: [linux,ubuntu,skill]
---

作为一个Ubuntu的初学者，之前参照[《鸟哥的Linux私房菜（基础学习篇）》](http://linux.vbird.org/linux_basic/ "在线版地址")折腾时出现了不少问题。凭印象整理了几个小问题，备忘和分享一下。环境：Ubuntu 11.10 64-bit

#### Ubuntu软件中心打不开，停在载入状态 ####

参考了 [http://zhangshijun0923.blog.163.com/blog/static/10266260820112250584912/](http://zhangshijun0923.blog.163.com/blog/static/10266260820112250584912/)

依次运行下面的命令：

`sudo apt-get update`

`sudo apt-get dist-upgrade`

`sudo apt-get install –reinstall software-center`

#### Ubuntu软件中心依然打不开，停在载入状态 & 更新管理器检查更新失败，出现提示“下载软件仓库信息失败，检查您的internet连接”，查看细节发现软件源报错 ####
参考了 [http://forum.ubuntu.org.cn/viewtopic.php?f=52&t=173860](http://forum.ubuntu.org.cn/viewtopic.php?f=52&t=173860)

移除旧源：

`sudo rm /var/lib/apt/lists/* -vf`

使用上述命令后运行“更新管理器”－“设置”－“Ubuntu软件”－“下载自”，换一个软件源。推荐使用中国的服务器，或者选择“自定义服务器”，在终端里输入：

`sudo gedit  /etc/apt/sources.list`

屏蔽掉出错的地方，加入163、sohu、台湾源之类速度较快的源，重新更新。 

#### 已经更换软件源，更新时依然报错，而且还是软件源报错 ####

打开sources.list，发现删掉的源又回来了。

经过研究是和之前安装的gnome3有关。查看/etc/apt ，sources.list.d文件夹里发现有gnome之类的文件，打开发现其中含有报错的源，删除它们。至此，终于可以更新了。

#### 为Chrome安装缺失flash插件 ####

参考了 [http://mtoou.info/ubuntu11-10-chrome-flash/](http://mtoou.info/ubuntu11-10-chrome-flash/)

基于64位linux的chrome浏览器没有自带flash播放器，默认的deb都是基于firefox的，所以要去Adobe下载adobe flash player 11 for linux 64bit的tar.gz包。下载完成后解压找到一个libflashplayer.so的文件，进入命令行，cd到放 libflashplayer.so文件的目录，执行：

`sudo mkdir /opt/google/chrome/plugins`    #在chrome的目录下建立插件文件夹

`sudo mv libflashplayer.so /opt/google/chrome/plugins/`    #剪切flashplayer到插件文件夹

Chromium中或：

`sudo mv libflashplayer.so /usr/lib/chromium-browser/plugins/`    #剪切flashplayer到插件文件夹