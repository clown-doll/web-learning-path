# 认识HTML文件

HTML 文件是有自己固有结构的，主要由两大部分组成，分别为：头部（head）和主体（Body）。其中，头部用来描述浏览器所需的信息，而主体则包含所要说明的具体内容。

接下来，让我们开始制作第一个网页

打开 Sublime Text 编辑器，快捷键 `Ctrl + N` 新建一个文档。快捷键 `Ctrl + Shift + P`，选择文档的语法模式 `Set Syntax: HTML`，然后在文档第一行输入`html:5`，按下tab，这样就完成了我们第一个网页的创建。

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        
    </body>
</html>
```

（备注：Sublime Text 需安装 Emmet 插件，才能这样快速建立一个网页。）

新生成的HTML的body部分是空的，没有任何内容，我们可以在里面添加一个标题及一段文字描述。

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>我的第一个网页</title>
    </head>
    <body>
        <h1>网页标题</h1>
        <p>我是网页主体内容。</p>
    </body>
</html>
```

将文件保存，我们就完成了第一个网页的书写。（ HTML文件的扩展名是`.html`或`.htm`）



## DOCTYPE声明

我们生成代码的第一行，是HTML为浏览提供的文档类型声明，告诉浏览器我们用的HTML是什么版本。这里我们使用的是 HTML5 的  DOCTYPE 声明。

HTML 4.01 提供了三种 DOCTYPE 声明 ： 过渡的\(Transitional\) 、严格的\(Strict\)、框架的\(Frameset\)，它们的写法都很长，难于记忆。由于 HTML5 的 DOCTYPE 声明简介，并且各种主流浏览器的解析模式相对最标准。所以我们这里推荐都`<!DOCTYPE html>`来声明 HTML 文档。对于其他几种声明，有兴趣的同学可以去 W3School 上查看[相关文档](http://www.w3school.com.cn/tags/tag_doctype.asp "HTML <!DOCTYPE> 标签")。

注意：

* DOCTYPE 声明必须放在每一个 HTML 文档第一行，在所有代码和标识之上；

* DOCTYPE 声明没有结束标签


## HTML文档结构

HTML 文档是一个树状结构。所有的网页标签都包裹在`<html></html>`标签中，它是整个文档的根节点。一个 HTML 文档的大体结构可以用下面这张图说明：

![](/assets/html2.png)

![](/assets/html.png)























标签语法

doctype



代码注释

