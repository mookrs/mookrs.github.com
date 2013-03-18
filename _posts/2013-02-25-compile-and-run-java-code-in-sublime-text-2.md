---
layout: post
title: "在 Sublime Text 2 中编译和运行 Java 代码（Windows）"
categories: Tech
tags: [Java, Sublime Text 2, Windows]
comments: yes
---
1\. 确保已经设置好 Java PATH

2\. 创建批处理文件

在 jdk 安装目录下的 bin 文件夹中新建一个 bat 格式的文件，命名为 javacexec.bat，内容如下：

<pre>
@ECHO OFF
cd %~dp1
ECHO Compiling %~nx1.......
IF EXIST %~n1.class (
DEL %~n1.class
)
javac %~nx1
IF EXIST %~n1.class (
ECHO -----------OUTPUT-----------
java %~n1
)
</pre>

3\. 修改 JavaC.sublime-build

进入 Sublime Text 2 安装目录下的 \Data\Packages\Java 文件夹，用文本编辑器打开 JavaC.sublime-build 文件，将 javac 修改成 javacexec.bat，如下：

<pre>
{

"cmd": ["javacexec.bat", "$file"],

"file_regex": "^(…*?):([0-9]*):?([0-9]*)",

"selector": "source.java"

}
</pre>

4\. 写好 Java 代码后 CTRL + B 即可编译运行

via <http://www.oschina.net/translate/compile-and-run-java-programs-in-sublime-text-2?cmp>