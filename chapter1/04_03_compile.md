# 编译

Sass 文件最终是要编译成 CSS 文件来引用执行的，有以下几种编译方式供大家选择。

## 命令编译

**单文件编译：**

```
sass <要编译的Sass文件路径>/style.scss:<要输出CSS文件路径>/style.css
```

**多文件编译：**

```
 sass sass/:css/
```

**实时编译：**

```
sass --watch <要编译的Sass文件路径>/style.scss:<要输出CSS文件路径>/style.css
```

## GUI界面工具编译

**Koala**

[koala](http://koala-app.com/) 是一个前端预处理器语言图形编译工具，支持Less、Sass、Compass、CoffeeScript，帮助web开发者更高效地使用它们进行开发。跨平台运行，完美兼容windows、linux、mac。

具体使用方法可以去github上看 [wiki](https://github.com/oklai/koala/wiki#docs) 。

## 编辑器编译

如果你使用的是webstorm，它本身内置了sass的编译。 

如果你使用的是sublime text，可以安装安装 sass 和 sass build 插件。安装成功后，可以按 `Ctrl+B` 进行编译。 

如果是其他编辑器，也可以对应搜索下是否有自动编译的功能或者有相应的插件可以使用。

## 在线编译

可以在 [sassmeister](http://www.sassmeister.com/) 进行在线编译。

## 自动化工具编译

像webpack、gulp 等自动化工具都有对应的插件来处理编译 Sass 文件，这里不做展开说明。到后续对应的课程里再详细介绍。



