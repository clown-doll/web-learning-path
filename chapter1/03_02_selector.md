# CSS选择器

在 CSS 中，选择器指明了我们所定义的样式将作用于哪个元素。前面的课程有介绍，CSS 代码由两大部分组成：选择器和属性声明：

```
选择器 {
    样式声明
}
```

这一小节将着重介绍，不同的选择器。

## 通用选择器

通用选择器是功能强大的选择器，使用星号（ `*` ）来表示，它将匹配 HTML 文档中所有标签元素。

```
* { color: red; }
```

这样设置后，HTML 文档中所有元素的文字颜色将全部为红色。

## 标签选择器

标签选择器其实就是 HTML 代码中的标签。这种选择器，大家应该比较熟悉了，在前面的例子，我们所用到的基本都是标签选择器。

```
p { font-size: 16px;}
```

上面代码定义的字体大小，将作用于所有 `<p>` 标签。

## 类选择器

通过设置元素的 class 属性，可以为元素指定类名。其语法为：

```
.类名 {
    样式声明
}
```

**语法介绍：**

* 类选择器是以英文句号（ `.` ）开头的

* 类名由开发者自己定义，尽量语义化，不能出现中文

* 文档中多个元素可以拥有同一个类名


**使用方法：**

* 将我们需要用样式控制的元素用标签包裹：`<span>CSS</span>`

* 为标签定义 class 属性：`<span class="red"></span>`

* 定义 red 类名下的样式：`.red { color: red; }`


具体来看一个例子：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>类选择器</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        .red { color: red; }
    </style>

</head>
<body>
    <p>在 <span class="red">CSS</span> 中，选择器指明了我们所定义的样式<span class="red">将作用于哪个元素</span>。</p>
</body>
</html>
```

![](/assets/css-selector-class.png)

定义了 `.red` 类的元素都显示了红色。

## ID选择器

ID选择器在形式上与类选择器有很多相似的地方，只不过它是通过元素的 id 属性来定义样式的。其语法为：

```
#id {
    样式声明
}
```

**语法介绍：**

* ID 选择器是以 `#` 开头的

* ID 由开发者自己定义，尽量语义化，不能出现中文

* 文档中 ID 是唯一的


**使用方法：**

* 将我们需要用样式控制的元素用标签包裹：`<span>CSS</span>`

* 为标签定义 id 属性：`<span id="tip"></span>`

* 定义 id 为 tip 的元素的样式：`#tip { color: red; }`


具体来看一个例子：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ID选择器</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        #tip { color: red; }
    </style>
</head>
<body>
    <p id="tip">在 CSS 中，选择器指明了我们所定义的样式将作用于哪个元素。</p>
</body>
</html>
```

![](/assets/css-selector-id.png)

我们为 `id = "tip"` 的元素定义了文字颜色为红色，因此 `<p>` 标签内文字颜色为红色。

## 属性选择器

属性选择器可以根据元素的属性及属性值来选择元素。

### 简单属性选择

如果希望选择有某个属性的元素，而不论属性值是什么，可以使用简单属性选择器。

```
E[attr] {
    样式声明
}
```

```
*[title] { color: red; }
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>属性选择器</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        *[title] { color: red; }
    </style>
</head>
<body>
    <p>
        在<a href="#" title="css">CSS</a> 中，选择器指明了我们所定义的样式将<strong title="stress">作用于哪个元素</strong>
    </p>
</body>
</html>
```

![](/assets/css-selector-attr.png)

在文档中，带有 `title` 属性的元素，文字都被设置为红色。

### 根据具体属性值选择

除了选择拥有某些属性的元素，还可以进一步缩小选择范围，只选择有特定属性值的元素。

```
E[attr=value] {
    样式声明
}
```

```
*[title="css"] { color: red; }
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>属性选择器-简单选择</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        *[title="css"] { color: red; }
    </style>
</head>
<body>
    <p>
        在<a href="#" title="css">CSS</a>中，选择器指明了我们所定义的样式将<strong title="stress">作用于哪个元素</strong>
    </p>
</body>
</html>
```

![](/assets/css-selector-attr2.png)

只有当 `title` 属性值为 `css` 时，才被选择。因此，上例中只有 CSS 文字显示为红色。

注意：这种格式要求**属性与属性值必须完全匹配**。否则将不能按照预期效果呈现。

### 根据部分属性值选择

如果需要根据属性值中的词列表的某个词进行选择，则需要使用波浪号（ `~` ）。

```
E[attr~=value] {
    样式声明
}
```

```
[title~="css"]
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>属性选择器-根据部分属性值选择</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        *[class~="red"] { color: red; }
    </style>
</head>
<body>
    <p>
        在 <a href="#" class="red link">CSS</a> 中，选择器指明了我们所定义的样式将<strong class="red">作用于哪个元素</strong>
    </p>
</body>
</html>
```



