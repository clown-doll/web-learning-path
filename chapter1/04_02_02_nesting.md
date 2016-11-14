# 嵌套

Sass 的嵌套有两种：

* 选择器的嵌套

* 属性的嵌套


## 选择器嵌套

所谓选择器嵌套指的是在一个选择器中嵌套另一个选择器来实现继承，从而增强了Sass 文件的结构性和可读性。

```
nav{
    line-height: 40px;
    a{
        display: block;
        padding: 0 10px;
        color: #fff;
    }
}
```

解析结果：

```
nav {
    line-height: 40px;
}
 
nav a {
    display: block;
    padding: 0 10px;
    color: #fff;
}
```

在嵌套的代码块内，还可以使用 `&` 引用父元素：

```
nav{
    line-height: 40px;
    a{
        display: block;
        padding: 0 10px;
        color: #fff;
        &:hover{
            color:#ddd;
        }
    }
}
```

解析结果：

```
nav {
    line-height: 40px;
}
 
nav a {
    display: block;
    padding: 0 10px;
    color: #fff;
}
 
nav a:hover {
    color: #ddd;
}
```

`&` 后面也可以直接加后缀：

```
#main {
    color: black;
    &-sidebar { border: 1px solid; }
}
```

解析结果：

```
#main {
    color: black;
}
 
#main-sidebar {
    border: 1px solid;
}
```

## 属性嵌套

所谓属性嵌套指的是有些属性拥有同一个开始单词，如 `border-width`，`border-color` 都是以 `border` 开头。具体看下面的例子：

```
p{
    border: {
        width: 4px;
        color: #888;
    }
}
```

解析结果：

```
p {
    border-width: 4px;
    border-color: #888;
}
```

**注意：border 后面也必须加冒号。**

## @at-root







