# Sublime Text

Sublime Text 是一款跨平台文本编辑器。它保留文本编辑器轻便的优点，并且扩展插件丰富，配置文件简单易迁移，深受广大开发者的喜爱。 现在主要的版本是 Sublime Text 2.0 和 Sublime Text 3.0。3.0版本稳定性跟2.0版本差不多，并且启动速度更快、持续完善更新，建议直接使用3.0的版本。

本文会介绍 Sublime Text 安装、配置、常用插件及快捷键。

## 安装

我们可以在 [Sublime Text 的官网](http://www.sublimetext.com/3)下载对应的安装包。

执行安装文件，选择安装路径：

![](/assets/sublime1.jpg)

添加到右键菜单：

![](/assets/sublime2.jpg)

安装完成后，首次打开 Sublime Text。在菜单栏 view -&gt; show sidebar，将侧边打开。

## 安装插件

Sublime Text插件有两种安装方式。

### 直接下载安装包安装

在菜单栏打开插件安装目录： Preferences -&gt; Browse Packages…，然后将自己下载的插件安装包解压后放到该目录即可。如果遇到插件不能运行，重启下Sublime Text。

### 通过Package Control安装

Package Control是在线安装插件的工具。在利用它安装插件前，需要先安装它。

**安装 Package Control** ：

1. 在菜单栏中调出console：view -&gt; show console （ctrl+\`）

2. 粘帖以下代码到底部命令行并回车进行安装：


```
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read()) 
```

**使用Package Control安装插件**：

1. 调出安装插件命令面板（Ctrl+Shift+P）

2. 输入install 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。


## 常用插件



