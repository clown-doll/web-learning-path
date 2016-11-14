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

`@at-root` 用来跳出选择器嵌套。**注意，**`@at-root`** 会跳出所有上级选择器。**

```
/*
* 没有跳出
*/
.parent-1 {
    color:#f00;
    .child {
        width:100px;
    }
}
 
/*
* 单个选择器跳出
*/
.parent-2 {
    color:#f00;
    @at-root .child {
        width:200px;
    }
}
 
/*
* 多个选择器跳出
*/
.parent-3 {
    background:#f00;
    @at-root {
        .child1 {
            width:300px;
        }
        .child2 {
            width:400px;
        }
    }
}
 
/*
* 跳出所有上级选择器
*/
.parent-4 {
    .child1 {
        width:300px;
        @at-root {
            .inner-child{
                width:400px;
            }
        }
    }
}
```

解析结果：

```
/*
* 没有跳出
*/
.parent-1 {
    color: #f00;
}
 
.parent-1 .child {
    width: 100px;
}
 
/*
* 单个选择器跳出
*/
.parent-2 {
    color: #f00;
}
 
.child {
    width: 200px;
}
 
/*
* 多个选择器跳出
*/
.parent-3 {
    background: #f00;
}
 
.child1 {
    width: 300px;
}
 
.child2 {
    width: 400px;
}
 
/*
* 跳出所有上级选择器
*/
.parent-4 .child1 {
    width: 300px;
}
 
.inner-child {
    width: 400px;
}
```

## @at-root \(without: …\)和@at-root \(with: …\)

默认 `@at-root` 只会跳出选择器嵌套，而不能跳出 `@media` 或 `@support`，如果要跳出这两种，则需使用 `@at-root (without: media)`，`@at-root (without: support)`。

这个语法的关键词有四个：`all`（表示所有），`rule`（表示常规css），`media`（表示media），`support`（表示support，因为 `@support` 目前还无法广泛使用，所以在此不表）。我们默认的 `@at-root` 其实就是 `@at-root (without:rule)`。

```
/*
* 跳出父级元素嵌套
*/
@media print {
    .parent1{
        color:#f00;
        @at-root .child1 {
            width:200px;
        }
    }
}
 
/*
* 跳出media嵌套，父级有效
*/
@media print {
    .parent2{
        color:#f00;

        @at-root (without: media) {
            .child2 {
                width:200px;
            } 
        }
    }
}
 
/*
* 跳出media和父级
*/
@media print {
    .parent3{
        color:#f00;

        @at-root (without: all) {
            .child3 {
                width:200px;
            } 
        }
    }
}
```

解析结果：

```
/*
* 跳出父级元素嵌套
*/
@media print {
    .parent1 {
        color: #f00;
    }
    .child1 {
        width: 200px;
    }
}
 
/*
* 跳出media嵌套，父级有效
*/
@media print {
    .parent2 {
        color: #f00;
    }
}
 
.child2 {
    width: 200px;
}
 
/*
* 跳出media和父级
*/
@media print {
    .parent3 {
        color: #f00;
    }
}
 
.child3 {
    width: 200px;
}
```

## @at-root与&配合使用

```
.child{
    @at-root .parent &{
        color:#f00;
    }
}
```

解析结果：

```
.parent .child {
    color: #f00;
}
```

## 应用于@keyframe

```
.demo {
    /*code ...*/    
    animation: motion 3s infinite;
    @at-root {
        @keyframes motion {
            /*code ...*/
        }
    }
}
```

解析结果：

```
.demo {
    /*code ...*/
    animation: motion 3s infinite;
}
 
@keyframes motion {
    /*code ...*/
}
```

