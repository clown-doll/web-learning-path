# Sublime Text

Sublime Text 是一款跨平台文本编辑器。它保留文本编辑器轻便的优点，并且扩展插件丰富，配置文件简单易迁移，深受广大开发者的喜爱。 现在主要的版本是 Sublime Text 2.0 和 Sublime Text 3.0。3.0版本稳定性跟2.0版本差不多，并且启动速度更快、持续完善更新，建议直接使用3.0的版本。

本文会介绍 Sublime Text 安装、配置、常用插件及快捷键。

## 安装

我们可以在 [Sublime Text 的官网](http://www.sublimetext.com/3)下载对应的安装包。

执行安装文件，选择安装路径：

![](/assets/sublime1.jpg)

添加到右键菜单：

![](/assets/sublime2.jpg)

安装完成后，打开 Sublime Text：

![](/assets/sublime4.jpg)

## 配置

Sublime Text使用JSON文件进行配置。在菜单栏 Preferences -&gt; settings -&gt;  User 里进行设置。

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

## 安装插件

## 常用快捷键

