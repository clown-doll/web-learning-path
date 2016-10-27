# 继承、层叠和特殊性

## 继承

CSS 的某些样式是具有继承性的，那么什么是继承性呢？从字面上也很好理解这个性质，即子标签的继承属性，如果没有指定值时，会默认取其上级标签的同属性值。来看一个例子：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>继承</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
    p { color: red; }
    </style>
</head>
<body>
    <p>子标签 <strong>继承</strong> 了上级标签的 CSS 样式属性</p>
</body>
</html>
```

![](/assets/css-inherit.png)

在上例中，我们只给 `p` 元素设置了字体颜色，但是从浏览器显示结果可以看出，其子标签 `strong` 同样也显示了红色，即子标签继承了父标签的 `color` 属性。

在 [w3c 这里](https://www.w3.org/TR/CSS22/propidx.html)有列出 CSS2.2 属性是否可继承。

## 层叠





