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

在浏览器中查看（右键 -&gt; Open in Browser ）的效果：

![](/assets/html3.png)

## DOCTYPE声明

我们生成代码的第一行，是HTML为浏览提供的文档类型声明，告诉浏览器我们用的HTML是什么版本。这里我们使用的是 HTML5 的  DOCTYPE 声明。

HTML 4.01 提供了三种 DOCTYPE 声明 ： 过渡的\(Transitional\) 、严格的\(Strict\)、框架的\(Frameset\)，它们的写法都很长，难于记忆。由于 HTML5 的 DOCTYPE 声明简介，并且各种主流浏览器的解析模式相对最标准。所以我们这里推荐都用`<!DOCTYPE html>`来声明 HTML 文档。对于其他几种声明，有兴趣的同学可以去 W3School 上查看[相关文档](http://www.w3school.com.cn/tags/tag_doctype.asp "HTML <!DOCTYPE> 标签")。

注意：

* DOCTYPE 声明必须放在每一个 HTML 文档第一行，在所有代码和标识之上

* DOCTYPE 声明没有结束标签


## HTML文档结构

HTML 文档是一个树状结构。所有的网页标签都包裹在`<html></html>`标签中，它是整个文档的根节点。一个 HTML 文档的大体结构可以用下面这张图说明：

![](/assets/html2.png)

![](/assets/html.png)

## 代码注释

有些时候我们会希望文档的某些内容暂时不显示，或者我们在制作网页的时候希望加入一些说明又不希望它们显示在页面上被用户看到，这时候我们就会用到HTML的注释。

我们将不希望被用户看到的内容放置在 `<!--` `-->` 之间，这就是 HTML 注释。

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>我的第一个网页</title>
    </head>
    <body>
        <!-- 这是我制作的第一个网页，mark下！ -->
        <h1>网页标题</h1>
        <p>我是网页主体内容。</p>
    </body>
</html>
```

保存，重新在浏览器中查看，发现看到的内容还是跟之前一样。嗯，注释了的内容是不会在浏览器中显示的。

关于HTML文件的基础知识就介绍到这里。接下来，我们会对HTML常用的标签做具体说明。

