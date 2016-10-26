# CSS选择器

在 CSS 中，选择器指明了我们所定义的样式将作用于哪个元素。前面的课程有介绍，CSS 代码由两大部分组成：选择器和属性声明：

```
选择器 {
    样式声明
}
```

这一小节将着重介绍不同的选择器。

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

通过设置元素的 `class` 属性，可以为元素指定类名。其语法为：

```
.classname {
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
    <p>
        在 <span class="red">CSS</span> 中，选择器指明了我们所定义的样式<span class="red">将作用于哪个元素</span>
    </p>
</body>
</html>
```

![](/assets/css-selector-class.png)

定义了 `.red` 类的元素都显示了红色。

## ID选择器

ID选择器在形式上与类选择器有很多相似的地方，只不过它是通过元素的 `id` 属性来定义样式的。其语法为：

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
    <p id="tip">
        在 CSS 中，选择器指明了我们所定义的样式将作用于哪个元素。
    </p>
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
    <title>属性选择器-简单选择</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        *[title] { color: red; }
    </style>
</head>
<body>
    <p>
        在 <a href="#" title="css">CSS</a> 中，选择器指明了我们所定义的样式将<strong title="stress">作用于哪个元素</strong>
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
    <title>属性选择器-根据具体属性值选择</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        *[title="css"] { color: red; }
    </style>
</head>
<body>
    <p>
        在 <a href="#" title="css">CSS</a> 中，选择器指明了我们所定义的样式将<strong title="stressed">作用于哪个元素</strong>
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

![](/assets/css-selector-attr.png)

上例中，两个元素的 `class` 属性都含有 `red` ，因此都显示为红色文字。

### 子串匹配属性选择

子串匹配属性选择器是指选择器能够匹配属性值的子串，主要有三种形式：

* `[attr^=value]`：选择带有以 attr 命名的，且值是以"value"开头的属性的元素。

* `[attr$=value]`： 选择带有以 attr 命名的，且值是以"value"结尾的属性的元素。

* `[attr*=value]`：选择带有以 attr 命名的，且值包含有"value"的属性的元素。


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>属性选择器-子串匹配</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        *[title*="ss"] { color: red; }
        *[title$="ed"] { font-weight: normal; }
        *[title^="cs"] { font-weight: 700; }
    </style>
</head>
<body>
    <p>
        在 <a href="#" title="css">CSS</a> 中，选择器指明了我们所定义的样式将<strong title="stressed">作用于哪个元素</strong>
    </p>
</body>
</html>
```

![](/assets/css-selector-attr3.png)

上例中，带有 `title` 属性的两个元素，其 `title` 值都含有 `ss` ，因此两个元素文字都显示为红色。另外，`title` 属性值以 `cs` 开头的元素加粗显示，`title` 属性值以 `ed` 结尾的元素字体不加粗。

### 特定属性选择类型

`[attr|=value]`：选择带有以 attr 命名的属性的元素，并且该属性是一个以空格作为分隔的值列表，其中至少一个值为"value"或者至少一个值以"value-"（"-"为连字符，Unicode编码为U+002D）开头。

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>属性选择器-特定选择</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        *[title|="css"] { color: red; }
    </style>
</head>
<body>
    <p>
        在 <a href="#" title="css">CSS</a> 中，选择器指明了我们所定义的样式将<strong title="css-stressed">作用于哪个元素</strong>。
    </p>
</body>
</html>
```

![](/assets/css-selector-attr.png)

上例中，两个元素的 `title` 属性值都符合条件，因此显示为红色文字。

## 后代选择器

后代选择器又可以称为包含选择器。

当使用空格连接两个元素时，便使得该选择器可以只匹配那些由第一个元素作为祖先元素的所有第二个元素\(后代元素\) 。后代选择器不需要相匹配元素之间要有严格的父子关系，只要是其后代元素即可。

语法：

```
E Y {
    样式声明
}
```

```
div a{ color: red; }
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>后代选择器</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        div a{ color: red; }
    </style>
</head>
<body>
    <div>
        <a href="#">后代选择器</a>
        <br>
        <p>在 <a href="#">CSS</a> 中，后代选择器不需要相匹配元素之间要有严格的父子关系</p>
    </div>
</body>
</html>
```

![](/assets/css-selector-afterworld.png)

上例中，`div` 元素的后代 `a` 元素，文字被设置为红色。

## 子元素选择器

如果不希望选择任意的后代元素，而是希望缩小范围，只选择某个元素的子元素，那么可以选择用子元素选择器。

子元素选择器使用了加号（ `>` ），其语法：

```
E > Y {
    样式声明
}
```

```
div > a{ color: red; }
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>子元素选择器</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        div > a{ color: red; }
    </style>
</head>
<body>
    <div>
        <a href="#">后代选择器</a>
        <br>
        <p>在 <a href="#">CSS</a> 中，后代选择器不需要相匹配元素之间要有严格的父子关系</p>
    </div>
</body>
</html>
```

![](/assets/css-selector-child.png)

上例中，只有第一个 `a` 元素是 `div` 元素的直接后代，因此，只有它显示为红色文字。

## 相邻兄弟选择器

如果需要选择紧接在另一个元素后的元素，而且二者有相同的父元素，可以使用相邻兄弟选择器。

相邻兄弟选择器使用了加号（ `+` ），其语法为：

```
E + Y {
    样式声明
}
```

```
h2 + p { color: red; }
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>相邻兄弟选择器</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        h2 + p { color: red; }
    </style>
</head>
<body>
    <h2>相邻兄弟选择器</h2>
    <p>如果需要选择紧接在另一个元素后的元素，而且二者有相同的父元素，可以使用相邻兄弟选择器</p>
    <p>相邻兄弟选择器使用了加号（+）</p>
</body>
</html>
```

![](/assets/css-selector-sibling.png)

相邻兄弟是需要紧邻的元素，因此，上例中，只有 `h2` 元素紧邻的 `p` 元素才被显示为红色。

## 伪类

伪类就是一种虚构的状态或者说是一个具有特殊属性的元素可以使用 CSS 进行样式修饰。伪类前面总是加一个冒号（ `:` ）。之后跟着伪类的名字或者是括号里面的值。常见的几种伪类是： `:link` ，`:visited` ， `:hover` ， `:active` 和 `:first-child` 。

伪类可以和 CSS 一起使用，定义不同状态下的样式。

**超链接的不同状态：**

```
a:link { color: red; } /* 未访问的链接 */
a:visited { color: green; } /* 已访问的链接 */
a:hover { color: pink; } /* 鼠标划过链接 */
a:active { color: #ccc; } /* 已选中的链接 */
```

注意：在 CSS 定义中，`a:hover` 必须被置于 `a:link` 和 `a:visited` 之后，才是有效的。`a:active` 必须被置于 `a:hover` 之后，才是有效的。

**选择第一个子元素：**

```
ul > li:first-child { color: red; }
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>伪类 - 第一个子元素</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        ul > li:first-child { color: red; }
    </style>

</head>
<body>
    <ul>
        <li>one</li>
        <li>two</li>
        <li>three</li>
    </ul>
</body>
</html>
```

![](/assets/css-selector-first-child.png)

## 伪元素

关于伪元素，它们更像是虚拟的元素可以和 HTML 元素一样对待。区别在于它们并不存在于文档树或者 DOM 之中。我们仍然可以使用 CSS 对其定义样式。常见的几种伪元素是： `:after` ， `:before` 。

**在元素的内容前面插入新内容：**

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>伪元素 - :before</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        p:before{ content: "before "; font-style: italic; color: #ccc; }
    </style>

</head>
<body>
    <p>伪元素</p>
</body>
</html>
```

![](/assets/css-selector-before.png)

**在元素的内容后面插入新内容：**

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>伪元素 - :after</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        p:after{ content: " after"; font-style: italic; color: #ccc; }
    </style>

</head>
<body>
    <p>伪元素</p>
</body>
</html>
```

![](/assets/css-selector-after.png)

选择器分组

我们经常会遇到这样的情况，希望A元素和B元素都拥有同样的样式，这时候我们就可以将选择器进行分组。我们通过英文逗号（ `,` ）来实现：

```
E, Y {
    样式声明
}
```

可以将任意多个选择器分组在一起，对此没有任何限制。

```
a, strong { color: red; }
```

上面的代码相当于

```
a { color: red; }
strong { color: red; }
```

一起来看一个完整的例子

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>选择器分组</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        a, strong { color: red; }
    </style>
</head>
<body>
    <p>
        在 <a href="#">CSS</a> 中，选择器指明了我们所定义的样式将<strong>作用于哪个元素</strong>
    </p>
</body>
</html>
```



