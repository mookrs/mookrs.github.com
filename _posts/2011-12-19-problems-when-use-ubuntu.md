---
layout: post
title: "解决使用Ubuntu时的几个小问题"
category: tech
tags: [linux, ubuntu, skill]
comments: yes
---

作为一个 Ubuntu 的使用者（*更新：现已转投 Fedora*），之前参照[《鸟哥的 Linux 私房菜（基础学习篇）》](http://linux.vbird.org/linux_basic/ "在线版地址")折腾时出现了不少问题。凭印象整理了几个小问题，备忘和分享一下。环境：Ubuntu 11.10 64-bit

#### 安装 Ubuntu 时卡在「正在探测文件系统」

安装前打开终端，硬盘安装输入  `sudo umount -l /isodevice`

光盘安装输入  `sudo umount -l /cdrom`

#### Ubuntu 软件中心打不开，停在载入状态

via <http://zhangshijun0923.blog.163.com/blog/static/10266260820112250584912/>

依次运行下面的命令：

`sudo apt-get update`

`sudo apt-get dist-upgrade`

`sudo apt-get install –reinstall software-center`

#### Ubuntu 软件中心依然打不开，停在载入状态

具体为：更新管理器检查更新失败，出现提示“下载软件仓库信息失败，检查您的 internet 连接”，查看细节发现软件源报错。

via <http://forum.ubuntu.org.cn/viewtopic.php?f=52&t=173860>

移除旧源：

`sudo rm /var/lib/apt/lists/* -vf`

使用上述命令后运行“更新管理器”－“设置”－“Ubuntu 软件”－“下载自”，换一个软件源。推荐使用中国的服务器，或者选择“自定义服务器”，在终端里输入：

`sudo gedit  /etc/apt/sources.list`

屏蔽掉出错的地方，加入 163、sohu、台湾源之类速度较快的源，重新更新。 

#### 已经更换软件源，更新时依然报错，而且还是软件源报错

打开 sources.list，发现删掉的源又回来了。

经过研究是和之前安装的 gnome3 有关。查看 /etc/apt ，sources.list.d 文件夹里发现有 gnome 之类的文件，打开发现其中含有报错的源，删除它们。至此，终于可以更新了。

#### 为 Chromium 安装缺失 Flash 插件

基于64位 Linux 的 Chromium 浏览器没有自带 Flash 播放器，默认的 deb 都是基于 Firefox 的，所以要去 Adobe 下载 adobe flash player 11 for linux 64bit 的 tar.gz 包。下载完成后解压找到一个 libflashplayer.so 的文件，进入终端，cd 到放 libflashplayer.so 文件的目录，执行：

`sudo cp libflashplayer.so /usr/lib/chromium-browser/plugins/`    # 拷贝 flashplayer 到插件文件夹