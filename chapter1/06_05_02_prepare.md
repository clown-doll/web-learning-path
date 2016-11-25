# 基础切割包

其实移动端跟手机端基础的切割包是类似的，只是在 HTML 模版上有些许差别。

## 目录结构

```
文件夹/
    ├── css/
    ├── js/
    └── image/
    └── pic/
    └── index.html
```

## 基础 HTML 模版

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="keywords" content=""/>
    <meta name="description" content=""/>
    <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no"/>
    <meta name="apple-mobile-web-app-capable" content="yes" />
    <meta name="apple-mobile-web-app-status-bar-style" content="black" />
    <meta name="format-detection" content="telphone=no, email=no" />
    <meta name="author" content="your name(number) | 2016-11-15">
    <title>title</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>

</body>
</html>
```

特别说明：

* `viewport` 的 `width` 属性通常设置为 PSD 设计稿的宽度，如 UI 提供的设计稿为 750，则 `width = 750`

* `author` 的 `content` 属性注明：姓名，工号，创建日期

* 这里仅为最基础的设置，如有更多其他需求，如强制 UC 浏览器全屏等需求，可以查看前面的 [meta 标签设置](/chapter1/06_05_01_meta.md)，进行对应的补充。


## 重置样式

样式重置可以参考前面 web 端的。

