# 调试

Sass 调试需要开启编译时输出调试信息和浏览器调试功能，两者缺一不可。

## 编译调试信息

目前 Sass 的调试分为两种，一种为开启 `debug-info`，一种为开启 `sourcemap`（这个将成为主流）。

* 如果开启的是 `debug-info`，则解析的css文件中会有以 `@media -sass-debug-info` 开头的代码，如没有则表明没有开启。 

* 如果开启的是 `sourcemap`，则在解析的css文件同目录下生成一个 `.css.map` 的后缀名文件。


两个的命令分别为 `–debug-info`，`–sourcemap`，开启如下：

```
sass --watch style.scss:style.css --debug-info
 
sass --watch style.scss:style.css --sourcemap
```

## koala开启调试信息

如下图：点击相应的文件，然后就会出现右边的编译选项，即可选择是否开启 `source map`，`debug info`：

![](/assets/koala-debug.png)

## 浏览器调试

### 谷歌浏览器调试

`F12` 打开调试面板，按快捷 `F1` 打开设置面板，在 `general` 选项中勾选 `Enable CSS source map` 和 `Auto-reload generated CSS`。

![](/assets/chrome-sass-debug.jpg)

点击 scss 文件，会跳到 source 里面的 scss 源文件，现在可以在里面进行修改，修改完成后可以右键选择 `save` 或 `save as` 命令，然后替换我们本地的 scss 源文件，刷新 chrome 就可以看到变化（注意，解析样式需要一定时间）。以后只要 `ctrl+s` 保存修改就可以在浏览器中看到修改效果了。

![](/assets/chrome-sass-debug3.jpg)

### 火狐浏览器调试

firefox 29 开始支持 `sourcemap`，注意是火狐自带的调试功能，而不是firebug。 

开启 `–sourcemap` 编译，右键 “查看元素” 采用火狐自带的调试功能，打开调试面板，在样式上右键选择 “显示原始来源” 。

![](/assets/firefox-debug1.jpg)

然后就可以进行我们的修改了，修改之后点击保存或者 `ctrl+s` 弹出我们要保存到哪里，直接覆盖到我们本地的源文件就ok了。

