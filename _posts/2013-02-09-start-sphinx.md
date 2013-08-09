---
layout: post
title: "使用 Sphinx 制作文档"
categories: Tech
tags: [Sphinx, Windows]
comments: yes
---

[Sphinx](http://sphinx-doc.org/) 是一个由 Python 编写的文档生成工具，可以用 [reStructuredText](http://wstudio.web.fc2.com/others/restructuredtext.html) 语法生成美观的文档。

1\. 确保已经安装 [Python](http://www.python.org/download/)

2\. 安装 [setuptools](https://pypi.python.org/pypi/setuptools)，以便使用 `easy_install` 命令

3\. 安装 Sphinx

`easy_install sphinx`

4\. Sphinx 使用

- 使用向导创建文档项目，执行 `sphinx-quickstart`

<pre>
Welcome to the Sphinx 1.1.3 quickstart utility.

Please enter values for the following settings (just press Enter to
accept a default value, if one is given in brackets).

Enter the root path for documentation.
> Root path for the documentation [.]:
// 输入根目录，默认为当前目录

You have two options for placing the build directory for Sphinx output.
Either, you use a directory "_build" within the root path, or you separate
"source" and "build" directories within the root path.
> Separate source and build directories (y/N) [n]:
// 是否分离 source 和 build 目录，默认「否」，我选择了「是」

Inside the root directory, two more directories will be created; "_templates"
for custom HTML templates and "_static" for custom stylesheets and other static
files. You can enter another prefix (such as ".") to replace the underscore.
> Name prefix for templates and static dir [_]:
// templates 和 static 文件夹的前缀，默认为下划线

The project name will occur in several places in the built documentation.
> Project name: // 项目名称
> Author name(s): // 作者名称

Sphinx has the notion of a "version" and a "release" for the
software. Each version can have multiple releases. For example, for
Python the version is something like 2.5 or 3.0, while the release is
something like 2.5.1 or 3.0a1.  If you don't need this dual structure,
just set both to the same value.
> Project version: 
> Project release []: 
// 项目版本号

The file name suffix for source files. Commonly, this is either ".txt"
or ".rst".  Only files with this suffix are considered documents.
> Source file suffix [.rst]:
// 源文件扩展名，默认为.rst

One document is special in that it is considered the top node of the
"contents tree", that is, it is the root of the hierarchical structure
of the documents. Normally, this is "index", but if your "index"
document is a custom template, you can also set this to another filename.
> Name of your master document (without suffix) [index]:

Sphinx can also add configuration for epub output:
> Do you want to use the epub builder (y/N) [n]:

Please indicate if you want to use one of the following Sphinx extensions:
> autodoc: automatically insert docstrings from modules (y/N) [n]:
> doctest: automatically test code snippets in doctest blocks (y/N) [n]:
> intersphinx: link between Sphinx documentation of different projects (y/N) [
:
> todo: write "todo" entries that can be shown or hidden on build (y/N) [n]:
> coverage: checks for documentation coverage (y/N) [n]:
> pngmath: include math, rendered as PNG images (y/N) [n]:
> mathjax: include math, rendered in the browser by MathJax (y/N) [n]:
> ifconfig: conditional inclusion of content based on config values (y/N) [n]:
> viewcode: include links to the source code of documented Python objects (y/N
[n]:

A Makefile and a Windows command file can be generated for you so that you
only have to run e.g. `make html' instead of invoking sphinx-build
directly.
> Create Makefile? (Y/n) [y]:
> Create Windows command file? (Y/n) [y]:

// 以上自己看着选就好
</pre>

- 工作目录列表

	> Makefile：一个包含指令的文件，在使用 make 命令时，可以使用这些指令来构建文档输出。
	>
	> _build：存放所生成的文件的目录。
	>
	>_static：不属于源代码的文件均存放于此处，稍后会在构建目录中将它们链接在一起。
	>
	> conf.py：这是一个 Python 文件，用于存放 Sphinx 的配置值，包括在终端执行 sphinx-quickstart 时选中的那些值。
	>
	> index.rst：文档项目的 root 目录。如果将文档划分为其他文件，该目录会连接这些文件。

- 生成 HTML

`make html`

因为 make 命令在我的 Windows 系统上不起作用，我写了下面这个 Python 脚本生成 HTML：

{% highlight python %}
#/usr/bin/env python
import subprocess
 
class RunCmd(object):
    def cmd_run(self, cmd):
        self.cmd = cmd
        subprocess.call(self.cmd, shell=True)
 
a = RunCmd()
a.cmd_run('sphinx-build -b html source build ')

raw_input()
{% endhighlight %}

- 其它

Sphinx 主题 <http://sphinx-doc.org/theming.html#builtin-themes>

参考链接：

[1]  [使用 sphinx 制作简洁而又美观的文档](http://www.ibm.com/developerworks/cn/opensource/os-sphinx-documentation/)

[2]  [Sphinx 1.1.2 documentation（中文）](http://sphinx-doc-zh.readthedocs.org/en/latest/)

[3]  [sphinx 使用及其简单配置](http://www.wlog.cn/geek/first-steps-with-sphinx.html)

[4]  [Sphinx Project How-To](https://code.google.com/p/pymotwcn/wiki/SphinxprojectHowto)