# 安装插件

Sublime Text插件有两种安装方式。

## 直接下载安装包安装

在菜单栏打开插件安装目录： Preferences -&gt; Browse Packages…，然后将自己下载的插件安装包解压后放到该目录即可。如果遇到插件不能运行，重启下Sublime Text。

## 通过Package Control安装

Package Control是在线安装插件的工具。在利用它安装插件前，需要先安装它。

### **安装 Package Control ：**

1. 在菜单栏中调出console：view -&gt; show console （ctrl+\`） 

2. 粘帖以下代码到底部命令行并回车进行安装：



`import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())`

![](/assets/sublime2_03.gif)

### **使用Package Control安装插件：**

1. 调出安装插件命令面板（Ctrl+Shift+P）

  ![](/assets/sublime3_03.gif)
2. 输入install 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。

  ![](/assets/sublime4_03.gif)

