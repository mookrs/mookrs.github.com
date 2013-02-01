---
layout: post
title: "Fedora 17 KDE 个人配置"
category: tech
tags: [linux, fedora, kde]
---

Gnome 用久了审美疲劳，身为懒人本打算转到 [Archbang](http://archbang.org/)，结果安装过程中没有 GUI 不敢继续碰了。于是受 [壳酱的蛊惑](http://shellex.info/why-i-use-kde-instead-of-gnome-1) 把 Fodora 16 Gnome 换成了 Fedora 17 KDE，一开始非常不顺手，现在用着用着也很不错。以下是配置过程中的记录。

#### 安装

我下载的镜像为 Fedora-17-x86_64-Live-KDE.iso，利用 [Universal USB Installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) 软件进行U盘安装。

#### 中文支持

应用程序 - 管理 - 语言 里选择「Chinese(P.R.China) - 中文(简体)」，系统会自动下载中文语言包。

system settings - locale - coutry/region & language - languages - 把「Chinese Simplified」 加到 「Prefered Languages」 并且按 apply。

输入法：应用程序 - 设置 - 输入法选择器，选择「使用IBus（推荐）」。

登陆界面换成中文：编辑 `/etc/sysconfig/i18n`

原来是 `LANG="en_US.UTF-8"`

添加 `LANG="zh_CN.UTF-8"`

#### 更新

更新系统和软件

`# yum update`

如果有问题可以试一下清除 yum 缓存

`# yum clean all`

#### 修复启动错误

Fedora 17 启动的时候，出现一条一闪而过的错误信息：

`GRUB2 error: file ‘/boot/grub2/locale/en.mo.gz’ not found`

解决办法是在 Konsole 中以 root 权限输入：

`# cp /usr/share/locale/en@quot/LC_MESSAGES/grub.mo /boot/grub2/locale/en.mo`

`# gzip /boot/grub2/locale/en.mo`

via <http://www.linuxidc.com/Linux/2012-08/69083.htm> & <https://bugzilla.redhat.com/show_bug.cgi?id=817187>

#### 界面美化

不像 gnome 那么麻烦，在 KDE 的 系统设置 - 应用程序外观 中即可调整风格、颜色和图标。

#### 中文美化

Fedora 的默认字体很渣，可以安装一个补丁改善。

`# rpm -Uvh http://www.infinality.net/fedora/linux/infinality-repo-1.0-1.noarch.rpm`

`# yum install freetype-infinality infinality-settings`

via <http://imobile365.com/articles/6331>

#### 使用微软雅黑字体

虽然在 Fedora 上装雅黑有点蛋疼，但是安装的话可以这样：

将雅黑字体复制到 `/usr/share/fonts/chinese/TrueType` 目录下。（`/chinese/TrueType` 是自己建立的路径）

修改字体权限，使 root 以外的用户可以使用这些字体。

建立字体缓存

`# cd /usr/share/fonts/chinses/TrueType`

`# mkfontscale`

`# mkfontdir`

`# fc-cache -fv`

重启即可。

via <http://www.selfcai.com.cn/2010/05/694.html>

#### fcitx 小企鹅输入法使用搜狗词库

专用于 fcitx-utf8 的词库下载地址：

fcitx-utf8 的搜狗词库精简版，仅整合搜狗词库、计算机词汇和诗词古句等：   
<http://hslinuxextra.googlecode.com/files/fcitx-sougou-phrase-small.7z>

fcitx-utf8 的搜狗词库，非常全面：<http://hslinuxextra.googlecode.com/files/fcitx-sougou-phrase-full.7z>

> 虽然 full 的这个词库很大，但是如果机器资源足够的话问题倒不大，响应速度没有太大影响。small 这个词库仅仅是搜狗官方词库、计算机专业词库、网络流行词和诗词古句等。
> 
> 如果你的 fcitx-utf8 是源代码安装的，只要把下载目录的 `pyPhrase.org` 替换掉原来的 `data` 目录下的同名文件再编译安装即可。
> 
> 如果你的 fcitx-utf8 是二进制包，那么用终端进入到下载目录中，执行 `./run.sh`，然后把生成的下列文件 `pybase.mb` 和 `pyphrase.mb` 复制到 `/usr/share/fcitx/data` 目录下覆盖原文件即可。（在 4.2.0 的 fcitx 中已经变成了 `/usr/share/fcitx/pinyin`）
> 
> 覆盖后请查看词库文件权限，可以设置为777，否则可能fcitx无法顺利调用词库文件。
>
> 加载词库需要时间，所以第一次使用反应会比较慢，但之后词库完全载入内存，速度就非常快了。

via <http://www.snowhawkyrf.name/2012/05/fcitx.html>

#### fcitx 输入法的一些个性设置

颜文字：使用 fcitx 的快速输入功能（按 `;` 键进入快速输入），建立 `～/.config/fcitx/data/QuickPhrase.mb` 文件，在里面加入自己喜欢的颜文字和对应的拼音。

特殊符号： 在 `~/.config/fcitx/pinyin/pySym.mb` 文件里定义。（里面已有例子）

更多设置查看下面的参考链接：

via <http://tieba.baidu.com/p/1769479692>

#### 关闭 Kwallet

Kwallet 是用来存密码的，连接无线网络时总会出现提示窗口，很烦人，于是我决定关了它。

点击「应用程序菜单」，搜索「Kwallet」。

点击 「Kwallet」而不是「KwalletManager」，前者是 KDE 密钥钱包的设定，后者是浏览钱包内存储的密码，完全打不开。

在设置页面勾选「启用 KDE 密钥钱包子系统（Enable the KDE Wallet subsystem）」

via <http://zh.opensuse.org/SDB:VPN_配置>

#### Konsole 光标漂移

貌似因为我把字体改了，Konsole 光标的出现了漂移。

暂时的解决方法：菜单栏 - 设置 - 配置当前方案 - 外观 - 字体 - 编辑字体，不选等宽而是选 DejaVu San Mono 或 Liberation Mono。

via <http://252376896.blog.163.com/blog/static/7820418220119162313789/>

#### 开机自动启动 Kwrite 并卡死

每次开机 Kwrite 总是自启动，然后造成系统卡死，kill 掉进程才正常。一怒之下卸载 Kwrite，连资源管理器都没了，以为能解决，结果换成了 Calligra Words 自启动。于是我怀疑系统是在试图用文本编辑器打开某个文件，可是总打不开。

果然，由于为了设置 GoAgent 开机启动在 `~/.kde/Autostart/` 中多了一项

`python ～⁄linux⁄software⁄goagent⁄proxy.py.desktop`

删除之，问题解决。

via <https://bugs.kde.org/show_bug.cgi?id=286658>

#### 修改 DNS

不喜欢用 ISP 提供的DNS。编辑 `/etc/resolv.conf` 中的内容，把 nameserver 后的数值改成自己的 DNS。

#### 视频播放

1.添加软件源

`# rpm -ivh http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm`

2.更新 yum 缓存

`# yum makecache`

3.安装播放器和解码器

`# yum install ffmpeg ffmpeg-libs gstreamer-ffmpeg xvidcore libdvdread libdvdnav lsdvd gstreamer-plugins-good gstreamer-plugins-bad gstreamer-plugins-ugly gstreamer-plugins-bad gstreamer-ffmpeg gnome-mplayer`

`＃ yum install ffmpeg ffmpeg-libs gstreamer-ffmpeg xvidcore libdvdread libdvdnav lsdvd`

`＃ yum install gstreamer-plugins-good gstreamer-plugins-bad gstreamer-plugins-ugly`

4.安装 mplayer 和 smplayer

`# yum install mplayer mplayer-gui smplayer`

成功安装 mplayer 后，配置一下再使用：

(1) 打开「mplayer」, 右键点击选择「Preferences」，打开设置界面；

(2) 「Video」 项选择「xv X11/Xv」；

(3)「Subtitles & OSD」->「Encoding」选择：「Simplified Chinese charset (CP936)」；

(4)「Font」->「Font」字体默认则可，也可选择喜欢的字体，「Encoding」: Unicode；

(5)「Codecs & demuxer」->「Video codec family」选择「FFmpeg's libavcodec codec family」，「Audio codec family」选择「FFmpeg/libavcodec audio decoders」。

另外，也可以到 mplayer 官网下载喜欢的皮肤，解压到 `/usr/share/mplayer/skins/` 即可。

via <http://blog.163.com/chfc2009@yeah/blog/static/130705634201251101755355/>

#### 安装 Chrome

在 `/etc/yum.repos.d/google-chrome.repo` 中加入

<pre>[google-chrome]
name=google-chrome - 64-bit
baseurl=http://dl.google.com/linux/chrome/rpm/stable/x86_64
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub</pre>

然后 `# yum install google-chrome-stable`

via <http://www.if-not-true-then-false.com/2010/install-google-chrome-with-yum-on-fedora-red-hat-rhel/>

#### 安装 FireFox

`# yum list firefox`

via <http://www.if-not-true-then-false.com/2011/install-firefox-on-fedora-centos-red-hat-rhel/>

#### 安装 LibreOffice

`# yum groupinstall "Office/Productivity"`

安装 LibreOffice 中文语言包

`# yum -y install  libreoffice-langpack-zh-Han*`

卸载 LibreOffice

`# yum remove libreoffice*`

via <http://wangye.org/blog/archives/626/>

#### 安装 Sublime Text 2

via <http://crabby.iteye.com/blog/1542141>
