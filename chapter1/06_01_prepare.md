# 基础切割包

通常情况下，我们会建立一个基础的切割包，每次项目都基于此进行丰富内容。

## 目录结构

```
文件夹/
    ├── css/
    ├── js/
    └── image/
    └── pic/
    └── index.html
```

* 文件夹的根目录中存放切割的 HTML 文件；

* css 文件夹中存放页面切割中使用到的样式表文件；

* js 文件夹中存放页面切割中使用到的 js 文件，jQuery 库等；

* image 文件夹中存放页面切割中使用的修饰性图片，如：背景图片、ICON图标等；

* pic 文件夹中存放页面切割中使用的内容性图片，如：广告图片，轮播图片等；


## 基础 HTML 代码

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="renderer" content="webkit">
    <meta name="description" content="">
    <meta name="keywords" content="">
    <meta name="author" content="your name(number) | 2016-11-15">
    <title>基础模板</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>

</body>
</html>
```

其中，`meta` 标签 `name` 值为 `author` 的部分，其 `content` 内容为：`姓名(工号) | 创建时间`。

### 重置样式

各个浏览器都有自己的默认样式，为了保证页面在各个浏览器下展示一致，通常我们都会将默认样式重置。

```
/* CSS Reset */
body, div, span, object, iframe,input, h1, h2, h3, h4, h5, h6, p, pre, a, acronym, address, code, del, em, font, img, ins, strong, b, i, dl, dt, dd, ol, ul, li, fieldset, form, label, table, tbody, tfoot, thead, tr, th, td{ padding: 0; margin: 0; }
table { border-collapse: collapse; border-spacing: 0; }
ins{ text-decoration: none;}
del{ text-decoration: line-through;}
input,select{ vertical-align:middle;}
input,textarea,select{font:12px/1.5 "microsoft yahei", Arial, sans-serif;}
fieldset, img { border: 0; }
address,code,th,em{font-style:normal;}
ol, ul { list-style: none; }
h1, h2, h3, h4, h5, h6 {font-size: 100%; font-weight: normal;}
```

这样我们的准备工作就都完成了。

