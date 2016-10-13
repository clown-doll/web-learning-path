# Sublime Text

Sublime Text 是一款跨平台文本编辑器。它保留文本编辑器轻便的优点，并且扩展插件丰富，配置文件简单易迁移，深受广大开发者的喜爱。 现在主要的版本是 Sublime Text 2.0 和 Sublime Text 3.0。3.0版本稳定性跟2.0版本差不多，并且启动速度更快、持续完善更新，建议直接使用3.0的版本。

本文会介绍 Sublime Text 安装、配置、常用插件及快捷键。

## 安装Sublime Text

我们可以在 [Sublime Text 的官网](http://www.sublimetext.com/3)下载对应的安装包。

执行安装文件，选择安装路径：

![](/assets/sublime1.jpg)

添加到右键菜单：

![](/assets/sublime2.jpg)

安装完成后，首次打开 Sublime Text。在菜单栏 view -&gt; show sidebar，将侧边打开。

![](/assets/sublime_03.gif)

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

![](/assets/sublime2_03.gif)

**使用Package Control安装插件**：

1. 调出安装插件命令面板（Ctrl+Shift+P）

  ![](/assets/sublime3_03.gif)

2. 输入install 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。

  ![](/assets/sublime4_03.gif)


## 常用插件

SideBarEnhancements：一款右键菜单增强插件。默认情况下，Sublime Text右键菜单功能很少。这个插件可以给Sublime Text的边栏菜单提供丰富的功能，包括：在工程中新建文件，移动文件，新窗口打开等。

Bracket Highlighter：用于匹配括号，引号和html标签。对于很长的代码很有用。安装好之后，不需要设置插件会自动生效。

ConvertToUTF8：支持 GBK, BIG5, EUC-KR, EUC-JP, Shift\_JIS 等编码的插件

Emmet：一个可以让你更快更高效地编写HTML和CSS，节省你大量时间的插件。它有[语法速查表](http://docs.emmet.io/cheat-sheet/)，可以帮助快速记忆简写形式。

CssComb：用于CSS属性排序和格式化的插件。该插件依赖Node.js环境，如果尚未安装Node.js，可以去其官网下载对应的版本进行安装。安装完成后，即可使用CssComb插件（ctrl + shift + c）。注意，CssComb不支持IE hack。

Autoprefixer

JsFormat

Alignment

DocBlockr

## 配置

Sublime Text使用JSON文件进行配置。在菜单栏 Preferences -&gt; settings -&gt; User 里进行设置。

以下是个人的配置文件，大家可以参考：

```
{
    // 删除你想要忽略的插件，需要重启
    "ignored_packages":
    [
        "Package Control",
        "Vintage"
    ],

    // 字号
    "font_size": 8,

    // 当前行高亮
    "highlight_line": true,

    // 行的上间距
    "line_padding_top": 2,

    // 行的下间距
    "line_padding_bottom": 2,

    // 制表位的对齐线
    "indent_guide_options": [ "draw_normal", "draw_active" ],

    // 开启选中范围内搜索
    "auto_find_in_selection": true,

    // 代码折叠按钮一直显示
    "fade_fold_buttons": false,

    // 自动移除行尾多余空格
    "trim_trailing_white_space_on_save": true,
    "trim_automatic_white_space": true,

    // 窗口失焦立即保存文件
    "save_on_focus_lost": true,

    // Tab键制表符宽度
    "tab_size": 4,

    // tab转空格
    "translate_tabs_to_spaces": true,

    // 有修改的tab高亮
    "highlight_modified_tabs": true,

    // 保存文件时是否删除每行结束后多余的空格
    "trim_trailing_white_space_on_save": true,

    // 自动换行
    "word_wrap": true,

    // 主题
    "theme": "Soda Dark.sublime-theme"
}
```

