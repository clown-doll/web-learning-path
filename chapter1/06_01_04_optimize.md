# 基础优化

我们在切割页面的时候，不是能将其切出来、展现无误就可以了，还得相对优雅、友好、可维护。

## 语义化

HTML 标签的使用应该遵循语义。例如，列表用 &lt;ul&gt; &lt;li&gt;；标题用 &lt;h1&gt; ~ &lt;h6&gt; 标签等。

具体可以查看 [《HTML 基础》](/chapter1/02_html.md) 教程，里面有介绍各种标签正确的使用方式。

HTML 5 标签提供了更丰富的语义化标签，在后续的进阶课程中，我们会为大家介绍。

前期，大家牢记能使用语义化的，尽量使用语义化标签。没有对应标签的，那就在样式命名上遵循语义化命名。尽量做到直观，简介易懂。

## 代码可维护性

由于我们身处团队中，每一项任务不单单只有我们自己独自负责，因此，这里要求大家书写的代码应该是可维护的。

有良好的缩进，清晰的注释，遵循团队内部代码规范。

规范详见：[《HTML 编码规范》](/chapter1/02_04_norm.md)和[《CSS 编码规范》](/chapter1/03_08_norm.md)

## 雪碧图

回顾前面切割页面的过程，每个小图标我们都是单独引用的。每一张图片都需要一个 HTTP 请求，和服务器链接一次，建立链接时需要额外时间的。为了减少 HTTP 请求数量，加速网页内容的显示，通常情况下，我们会将一些小图标作为背景，并且利用 CSS Sprite 雪碧图技术将图片合并为一张相对较大的图片。

### **什么样的图片适合雪碧图？**

并不是所有图片都需要做成雪碧图的，通常情况下，我们考虑以下几点，来判断图片是否需要做成雪碧图：

* 静态图片，不随用户内容变化而变化，即装饰性图片

* 小图片，图片内容较小

* 加载量比较大


### **实现原理**

雪碧图的基本原理是把网站上用到的一些图片整合到一张单独的图片中，将改图作为背景图片引入，并使用 `background-position` 属性定义需要显示的背景图。

![](/assets/web-layout-sprite.png)

之前我们有使用到这几个图片的地方，对应的 `background` 和 `background-position` 都发生相应的变化：

```
.header{ background: url(../image/sprite.png) repeat-x 0 0;}
```

```
.logo{ background: url(../image/sprite.png) no-repeat -610px -91px;}
```

```
.sidebar-title{ background: url(../image/sprite.png) no-repeat 0 -88px;}
```

```
.main-title{ background: url(../image/sprite.png) no-repeat 0 -160px;}
```

```
.main-list .times{ background: url(../image/sprite.png) no-repeat -292px -103px;}
```

## 图片优化

除了将小图合并为雪碧图之外，我们对站上所有能用到的图片都需要做一定优化。

质量上，通常：

* `.jpg` 质量保存为 `60%` 左右，单张图片 k 数控制在 `150k` 以下，banner与大背景等除外。

* .png 图片也得使用工具进行进一步压缩。常用的在线压缩工具：[TinyPNG](https://tinypng.com/)


## 基础seo

其实前面提到的语义化也是前端 seo 的一个体现，除此之外，还有我们可以做的事情。

### **meta**

`<meta>` 标签定义了文档的各种元数据，一些有助于 SEO 优化。（对这部分内容如果感觉陌生，可以查看前面的教程：[《HTML基础-文档和元数据标签》](/chapter1/02_02_00_doc.md)）

`keywords`，`description` 分别定义了网页的关键字和站点描述，在平常页面制作时，不能忽略。

```
<meta name="description" content="福建终身学习在线给社区公民、老年人、中专-职专，工人农民提供一个在线学习、继续教育、终身教育、终身学习的平台，大家可以在这里通过培训视频、培训教程在线学习，远程教育，我们致力打造高效的福建省终身学习在线网。">
```

```
<meta name="keywords" content="福建终身学习在线、继续教育、成人教育、终身教育培训视频、终身学习">
```

### **title**

站点 `<title>` 的规则为：`页面标题-站点标题-站点域名`

```
<title>课程分类 - 女职工周未学习网 - nzg1.fj51e.cn</title>
```

### img

`<img>` 标签统一加上 `alt` 属性。避免在图片不能正常加载时，有相应的文字说明。

同时，图片加上 `width` 和 `height` 属性，避免图片加载过程中，页面错乱排布。

### a

`<a>` 标签加上 `title` 属性。有利于鼠标进过是显示完整文字内容。

---

更多更细节的问题，查看内部《CheckList》。

每次切割完成后，都必须按照 CheckList 列出的项目，一一检查。

