# 继承、优先级和层叠

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

## 优先级

我们知道，一个元素的样式可以通过多种方式来定义， 那么最终是什么决定了元素显示在浏览器中的样式呢？CSS 优先级会决定 CSS 样式在浏览器中被解析的先后顺序。

CSS优先级规则

样式表中的特殊性描述了不同规则的相对权重，这些权重决定了优先级，它的基本规则是：

* 继承权值为0.1（忽略不计）

* 标签的权值为1

* 类选择器的权值为10

* ID 选择器的权值为100


权值越高，优先级越高。例如：

```
p { color: #999; } /* 权值：1 */
p strong { color: #333; } /* 权值：1 + 1 = 2 */
#stress{ color: red; } /* 权值：100 */
#stress i.italic{ color: pink; } /* 权值：100 + 1 + 10 = 111 */
```

假设有一段文字，它的 HTML 结构为：

```
<p>浏览器根据<strong>优先级</strong>解析 <strong id="stress"><i class="italic">CSS</i> 样式属性</strong></p>
```

那么根据上面的样式定义，最终浏览器解析后，应该呈现为：

![](/assets/css-priority.png)

## 层叠

优先级决定了浏览器的解析，那么，如果权重值相同的情况下，浏览器又将如何解析呢？





























