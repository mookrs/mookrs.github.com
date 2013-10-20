---
layout: post
title: "ArcGIS for Android 开发：Android 平台搭建"
categories: Tech
tags: [ArcGIS, Android]
comments: true
---

前言：《ArcGIS for Android 开发》这几篇文章本来是我为师弟写的一份入门指导。水平有限，难免有错误之处，欢迎指正，仅供参考。 :)

## 清单：

JDK + Eclipse + Android SDK + ADT + ArcGIS Runtime SDK for Android

## 一、安装 JDK

### 1.下载 JDK

JDK（Java Development Kit）是 Oracle 公司针对 Java 开发人员发布的免费 SDK（Software Development Kit）。JDK 有多个类型版本，这里我们选择 Java SE（Standard Edition，标准版）。

JDK 的下载地址在 <http://www.oracle.com/technetwork/java/javase/downloads/index.html>，其页面如下图：

![](/static/img/2013/06/Java-SE-Downloads.png)

选择 Java Platform (JDK) 7u17，点击它的 DOWNLOAD 按钮，跳转到新的页面：
 
![](/static/img/2013/06/Java-SE-Development-Kit-7-Downloads.png)

这里有不同平台的版本可供下载，对于 Windows 系统分为 32 位（x86）和 64 位（x64）两种。我的电脑是 64 位 Windows 7 操作系统，所以选择下载 jdk-7u17-windows-x64.exe。下载相应版本的安装包前，需要接受相应的许可协议，默认是不接受许可协议（Decline License Agreement），必须先点击左边的单选按钮 Accept License Agreement，接受许可协议才能下载。

### 2.安装 JDK

如果下载的是 exe 可执行程序，只需要运行该程序进行安装，无需设置环境变量，在安装过程中可以指定安装的路径。当然你也可以检查一下环境变量设置得是否正确，可以新建或修改环境变量：

1）开始 → 计算机 → 属性 → 高级系统设置 → 环境变量 → 系统变量 → 新建/编辑

2）配置变量

* 变量名：JAVA_HOME

* 变量值：D:\Java\jdk1.7.0_11（JDK 的安装路径，我这里是 D:\Java\jdk1.7.0_11） 

* 变量名：PATH 

* 变量值：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin 

* 变量名：CLASSPATH 

* 变量值：.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\toos.jar

![](/static/img/2013/06/Environment-Variables.png)

### 3.验证环境变量

Win+R 输入 `cmd` 运行命令提示符窗口，在命令提示符窗口中输入 `java -version` 后按回车键，验证 Java 的环境变量是否配置成功。如果成功，会显示出相应的 Java 版本，例如我的 Java 版本为 1.7.0_11：

![](/static/img/2013/06/Java-Version.png)

## 二、安装 Eclipse

配置好 JDK 后，就可以开始配置 Android 的集成开发环境（IDE）了。官方推荐的 IDE 为 Eclipse，所以我们就以 Eclipse 作为 IDE。Eclipse 在 <http://www.eclipse.org/downloads/> 可以下载，我下载的版本是 Eclipse Classic 4.2.2 的 Windows 64 Bit 版本。

![](/static/img/2013/06/Eclipse-Downloads.png)

选择相应版本后进入下载页面，里面有许多链接，这是由于 Eclipse 下载的用户特别多，为了缓解主服务器的压力，官方提供了很多镜像站点，系统会根据用户电脑的 IP 自动选择最佳的镜像站点，如下图所示：

![](/static/img/2013/06/mirror-selection.png)

点击 [China] Northeastern University (http) 链接就可以下载了。Eclipse 是绿色软件，下载后的文件是一个 zip 压缩包，解压后直接运行 eclipse.exe 即可使用。

## 三、安装 Android SDK

### 1.下载 Android SDK

Android SDK 可到 Android Developers 官网 <https://developer.android.com/sdk/index.html> 下载。因为我们已经安装了 Eclipse，所以要选择下方的 USE AN EXISTING IDE，点击 Download the SDK Tools for Windows。

![](/static/img/2013/06/Download-Android-SDK.png)

然后勾选 I have read and agree with the above terms and conditions，同意许可协议，即可下载 Android SDK。我下载的版本为 installer_r21.1-windows.exe。

![](/static/img/2013/06/agree-android-sdk-terms.png)

### 2.设置环境变量

* 变量名：PATH

* 变量值：Android SDK 中 platform-tools 文件夹的绝对路径（例如我的位置为 D:\Program Files (X86)\Android\android-sdk\tools）

### 3.检查 Android SDK 是否安装成功

设置好 Android SDK 的环境变量后，进入命令提示符窗口，运行 `android -h`。如果有类似以下的输出，表明安装成功：

![](/static/img/2013/06/android-h.png)

### 4.安装开发所用的包

从开始菜单打开 SDK Manager，勾选需要的工具和 API，选择 Install packages。

![](/static/img/2013/06/Android-SDK-Manager.png)

点击 Accept License 同意用户协议，Install 开始安装。

![](/static/img/2013/06/Choose-Packages-to-Install.png)

## 四、安装 ADT 插件（Android Development Tool）

打开 Eclipse，在菜单中选择 Help → Install New Software，在弹出的 Install 窗口中点击右上方的 Add 按钮，在 Location 栏目中加入 ADT 的下载地址：<https://dl-ssl.google.com/android/eclipse/>，Name 栏目可以填写也可以不填写。然后点击 OK： 

![](/static/img/2013/06/Install-ADT.png)

如果成功访问 Google 的相关服务器，会显示获取的 ADT 插件信息，全部选中里边的复选框：

![](/static/img/2013/06/ADT-Information.png)

点击 Next 按钮，会显示详细情况：

![](/static/img/2013/06/Install-Details.png)

继续点击 Next 按钮，会要求用户同意 License，默认为不同意，且下面的 Finish 按钮为灰，确保选中同意 License，然后点击 Finish 按钮：

![](/static/img/2013/06/Review-Licenses.png)

然后就进入 ADT 的下载安装过程中，根据用户的网络速度请耐心等待。如下图所示：

![](/static/img/2013/06/Install-Software.png)

如果出现警告信息，提示有未签名的插件，点击 OK 即可：

![](/static/img/2013/06/Security-Warning.png)

一旦下载安装成功会提示重启 Eclipse，点击 RestartNow 按钮重启 Eclipse。

如果在上面的安装下载的过程中失败了，尝试重复上面的过程。如果不能访问 <https://dl-ssl.google.com/android/eclipse/> 的话就改用 <http://dl-ssl.google.com/android/eclipse/>，通常两个总有一个可以用，或者两个链接地址都可以用。仍然无法访问，挂上 VPN。

最后打开 Eclipse 菜单中的 Window → Preferences，点击左侧的 Android，然后在右边 SDK Location 处设置 Android SDK 的位置，如图：

![](/static/img/2013/06/SDK-Location.png)

## 五、安装 ArcGIS Runtime SDK for Android
    
ArcGIS Runtime SDK for Android 是 Esri 为开发者提供的 Android 应用开发工具包，内置了大量 API，可以从 Esri 官网下载插件，在本地进行安装。官网的插件下载地址为：<http://developers.arcgis.com/en/android/>，当前版本的文件为 ArcGISAndroidSDK_v10.1.1.zip，安装方法与 ADT 插件类似。在 Eclipse 菜单中选择 Help → Install New Software，在弹出的 Install 窗口中点击右上方的 Add 按钮，在弹出窗口中点击 Archive，选择已经下载的 ArcGISAndroidSDK_v10.1.1.zip 压缩包，完成安装即可。

![](/static/img/2013/06/Install-ArcGIS-Runtime-SDK-for-Android.png)

安装完成并重启 Eclipse 后，打开菜单 File → New → Project…，可以看到在 New Project 中，已经有 ArcGIS for Android 可供选择，说明 ArcGIS Runtime SDK for Android 已经安装成功。

![](/static/img/2013/06/New-Project-ArcGIS-for-Android.png)

## 六、使用虚拟设备（AVD）或真机进行开发

### 1.使用 AVD

在使用 Android 模拟器进行开发时，由于对 OpenGL ES2.0 的要求，需要模拟器支持 GPU。Android 4.0.3 及以上版本的模拟器提供对 GPU 的支持，所以要使用 Android 4.0.3 以上版本的模拟器。

在 Eclipse 中打开 Android Virtual Device Manager（工具条上手机里的小绿人），新建一个 AVD。Device 我们选择较为常见的 4.0"，Target 选择 4.1.2，CPU/ABI 选择 ARM（armeabi-v7a），RAM 设置为 768，Emulation Options 中勾选 Use Host GPU，如下图所示：

![](/static/img/2013/06/New-AVD.png)

我们可以在菜单的 File → New → Project... 中找到 ArcGIS Samples for Android，新建一个 Demo 测试 AVD。

![](/static/img/2013/06/ArcGIS-Sample-for-Android.png)

**注意：因为我们安装的是 JDK 1.7（JDK 1.7 即 JDK 7），而 Android 默认使用的是 JDK 1.6，所以在运行前要在项目文件夹上单击鼠右键，选择 Android Tools → Fix Project Properties，将编译器改为 1.6 版本。另外，例子的 project.properties 文件中是 `target=android-10`，代表着使用的 Androd SDK 版本是 2.3.3，如果你没有安装 Android 2.3.3 的 API ，一定要改成自己使用的 API，例如 Android 4.1.2 对应的要改为 `target=android-16`**

在项目文件夹上单击鼠标右键，选择 Run As → Android Application 即可运行。

### 2.使用真机

如果有 Android 设备的话强烈建议用真机开发，AVD 除了占内存外运行的速度也十分糟糕。ArcGIS Runtime SDK for Android 对 Android 设备有些基本要求：Android 版本 2.2 及以上，支持 OpenGL ES2.0。除此之外，与一般 Android 项目在真机上开发没有区别。

将 Android 设备通过数据线与电脑 USB 接口连接，在 Android 系统设置的「开发选项」中，选中「USB调试」。运行程序，程序会上传到已连接好的 Android 设备，并自动安装运行。

参考资料：

[1] 如何在 Windows 环境下安装 JDK <http://wiki.eoe.cn/page/Install_JDK_in_Windows>

[2] 配置 Android SDK 开发环境 <http://wiki.eoe.cn/page/Eclipse_Configure.html>

[3] 【教程连载】ArcGIS Runtime for Android开发教程V2.0（2）开发环境配置 <http://blog.csdn.net/arcgis_all/article/details/8232984>