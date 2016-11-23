# 布局模型

在前面的章节中，我们了解了 CSS 盒模型的基本概念。在这基础上，我们就可以开始对布局模型的学习了。CSS 布局模型定义了网页布局的架构，是对网页的外在表现。

CSS 包含 3 种基本布局模型：

* 流动模型

* 浮动模型

* 层模型


## 流动模型

默认情况下，HTML 元素都是根据流模式来分布的。

观察我们之前的所有例子，我们可以很容易观察处理，流动布局模型有两个比较典型的特征：

* 块状元素会在所处的包含元素内自上而下按顺序垂直延伸分布。因为在默认状态下，块状元素的宽度都是100%。实际上块状元素都会以行的形式占据位置。

* 在流动模型下，内联元素都会在所处的包含元素内从左到右水平分布显示。


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>布局模型 - 流动布局模型</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        .wrapper{
            width: 600px;
            border: 1px dashed red;
        }
        h1 span{
            font-size: 14px;
        }
        h1, p{
            background-color: yellow;
        }
        span, strong{
            background-color: #f5f5f5;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <h1>流动布局 <span> - h1</span></h1>
        <p>块状元素都会在所处的包含元素内自上而下按顺序垂直延伸分布。 <span> - p</span></p>
        <p>
            <span>我是内联元素 - span</span>，
            内联元素会在所处的包含元素内<strong>从左到右水平分布显示  - strong</strong>
            <span> - p</span>
        </p>
    </div>
</body>
</html>
```

![](/assets/css_layout_flow.png)

如上图所示，最外层是块级元素 `div`，设置宽度 `600px`。`div` 里分别包裹着 `h1`, `p` 元素，这里用换色背景标识，很明显他们都是块级元素，独占一行。在块级元素内，又用 `span` 标注其父级是什么标签，`span` 是内联元素，这里用浅灰色背景标识，在其父元素内，从左到右水平分布显示。

关于块级元素，行内元素，我们在之前的课程中有介绍过，这里就不重复介绍。大家可以查看《[HTML 基础 - 标签分类](/chapter1/02_03_type.md)》回忆相关内容。

## 浮动模型

从前面的流动布局可以看出，块级元素都是独占一行的，那么加入我们希望让两个块级元素并排显示，应该怎么做呢？这就涉及到即将要讲的浮动模型了。

所谓的浮动模型，是利用 `float` 属性，将块级元素定义为浮动。浮动元素能像内联元素一样，在同一行显示。

我们一起看一个例子：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>布局模型 - 浮动布局模型</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        .wrapper{
            width: 300px;
            border: 1px dashed red;
        }

        div.inner {
            float: left;
            width: 100px;
            height: 100px;
            margin: 10px;
            background-color: red;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="inner"></div>
        <div class="inner"></div>
    </div>
</body>
</html>
```



