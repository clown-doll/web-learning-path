# CSS 概览

前面我们已经学习了 HTML 基础知识。但是我们从未涉及过布局及样式，所有 HTML 元素都是随意的放置在我们的网页代码中。仅凭浏览器的默认样式，我们做的网页似乎不那么美观。那么，在接下来的时间内，我们就学习 CSS 相关知识，让我们的网页变得更美观灵活。

## 什么是CSS？

CSS全称为“ 层叠样式表 \(Cascading Style Sheets\) ”，它主要是用于定义 HTML 内容在浏览器内的显示样式，如文字大小、颜色、字体加粗等。

如下列代码：

```
p{
    padding: 100px;
    font: 14px "Microsoft YaHei", Verdana, sans-serif;
}
```

## 为什么使用CSS？

我们可以一起对比下，有设置样式跟没设置样式，浏览器展示的区别：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>认识css样式</title>
    <style>
        .parent{
            margin: 40px auto 0;
            padding: 20px;
            width: 500px;
            border: 1px dashed red;
        }
        p{
            color: green;
        }
        .inner{
            font: 14px "Microsoft YaHei", Verdana, sans-serif;
        }
        h3{
            font-family: "Microsoft YaHei", Verdana, sans-serif;
        }
    </style>
</head>
<body>


<div class="parent">
    <h3>p 标签定义字体：</h3>
    <p class="inner">CSS全称为“ 层叠样式表 (Cascading Style Sheets) ”，它主要是用于定义 HTML 内容在浏览器内的显示样式，如文字大小、颜色、字体加粗等。</p>
</div>

<div class="parent">
    <h3>p 标签未定义字体：</h3>
    <p>CSS全称为“ 层叠样式表 (Cascading Style Sheets) ”，它主要是用于定义 HTML 内容在浏览器内的显示样式，如文字大小、颜色、字体加粗等。</p>
</div>


</body>
</html>
```

![](/assets/css-understand.png)

从上面的例子可以看出，利用CSS，我们就可以控制网页元素的展示，并且能够通过定义某一个样式，让不同位置的元素有着统一的字体，边距等。它使页面更加灵活，同时它可以根据不同的浏览器，而达到显示效果的统一和不变形，也可以根据使用者的屏幕尺寸进行适当的网页宽度调整。

