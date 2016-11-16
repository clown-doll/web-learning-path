# 页面布局

经过前面对 PSD 的分析，我们就可以开始正式切割页面了。

## 搭建框架

根据前面的分析，这个页面主体结构如下：

![](/assets/full_psd2.jpg)

按照划分的5个区域，书写对应的 HTML 代码：

```
<!-- header -->
<div class="header">
    <div class="wrapper">
        header
    </div>
</div>
<!-- /header -->
<!-- flash -->
<div class="flash">
    banner
</div>
<!-- /flash -->

<!-- container -->
<div class="wrapper container clearfix">
    <div class="sidebar">
        sidebar
    </div>
    <div class="main">
        main
    </div>
</div>
<!-- /container -->

<!-- footer -->
<div class="footer">
    footer
</div>
<!-- /footer -->
```

在 `header` 里面定义了一个名为 `wrapper` 的样式，是因为头部主体内容在 `960px` 内，我们用这个限制内容分布。

对应前面主体结构的 CSS 代码：

```
/*------------ public ------------*/
body{ background-color: #fff; font: 14px "SimSun"; color: #333;}
.wrapper{ margin: 0 auto; width: 960px; }
/* link */
a{ color:#333; text-decoration:none;}
a:hover{ color:#cd5d00;}

/*------------ header ------------*/
.header{ height: 88px;}

/*------------ flash ------------*/
.flash{ height: 339px;}

/*------------ container ------------*/
.container{ margin-top: 27px; }
/*sidebar*/
.sidebar{ float: left; width: 268px; }
/*main*/
.main{ float: right; width: 661px; }

/*------------ footer ------------*/
.footer{ margin-top: 25px; height: 106px; }
```

这样整个页面的整体框架就出来了。

接下来，我们就细化到局部，分别讲解。

## header 切割

### 结构分析

观察 PSD 可以看出，`header` 部分有一个渐变背景，并且结构上可以分为左边的 `logo` 和右边的 `nav` 两个模块。

![](/assets/header_bg1.jpg)

对应的 HTML 代码：

```
<!-- header -->
<div class="header">
    <div class="wrapper">
        <h2 class="logo"></h2>
        <ul class="nav"></ul>
    </div>
</div>
<!-- /header -->
```

CSS 书写分析：

* `header` 的背景可以运用图片横向循环来处理，前期我们已经切割出可循环平铺的背景图片；

* `logo` 部分左浮动。为了强调站点名称，我们会使用具有一定权重的 h2 标签；

* `nav` 的整体宽度大致为 580px，并且向右浮动；


```
.header{ height: 88px; background: url(../image/bg-header.png) repeat-x 0 0;}
.logo{ float: left; width: 304px; }
.nav{ float: right; width: 580px; }
```

### logo 结构分析

![](/assets/logo.png)

`logo` 这块主要由两部分组成：

* logo 图片

* 站点文字


由于通常 `logo` 都需要可点击，并且指向站点首页，所以，这块还需要为其填充 `<a>` 标签链接。

对应的 HTML 代码：

```
<h2 class="logo">
    <a href="#" title="福建终身教育-女职工周未学习网">
        福建终身教育 
        <strong>女职工周未学习网</strong>    
    </a>
</h2>
```

CSS书写分析：

* logo 图片不经常替换，所以这部分可以作为背景图片处理。其大小为 51\*57，整个 logo 部分的高度将参照图片高度。

* 文字分为上下两部分，项目名称及站点名称。上部分文字为宋体、14px，下部分文字为微软雅黑、30px。


对应的 CSS 代码：

```
.logo{ float: left; width: 304px; background: url(../image/logo.png) no-repeat left center;}
.logo a{ display: block; padding: 14px 0; height: 57px; padding-left: 59px;}
.logo a strong{ display: block; font-size: 30px; font-family: "Microsoft YaHei"; font-weight: normal;}
```

### nav 结构分析

![](/assets/nav_bg.jpg)

`nav` 有5个导航地址组成，我们可以使用 `<ul>` 列表来组织对应的内容，并且里面都需要添加链接。每个连接都有打开的状态，可以为这个状态添加 `active` 样式。

对应的 HTML 代码：

```
<ul class="nav">
    <li>
        <a href="#" title="">首页</a>
    </li>
    <li>
        <a href="#" title="">课程推荐</a>
    </li>
    <li class="active">
        <a href="#" title="">课程分类</a>
    </li>
    <li>
        <a href="#" title="">新闻公告</a>
    </li>
    <li>
        <a href="#" title="">关注女职工</a>
    </li>
</ul>
```

CSS 书写分析：

* 每个导航项对应一个 `<li>` 标签，每个 `<li>` 标签里有 `<a>` 标签作为链接。

* `<a>` 标签根据文字自适应宽度，文字大小为 18px，字体为“微软雅黑”。

* 导航的选中项底部有个小三角图标，利用样式实现


对应的 CSS 代码：

```
.nav{ float: right; margin-top: 8px; width: 600px;}
.nav li{ display: inline-block; padding-left: 46px; font-family: "Microsoft YaHei"; font-size: 18px;}
.nav li a{ position: relative; display: block; padding: 28px 0;}
.nav li a:hover:after,
.nav .active a:after{ content: ""; display: block; position: absolute; bottom: 0; left: 50%; margin-left: -10px; width: 0; height: 0; border-style:solid; border-width: 10px;border-color: transparent transparent #f28f26 transparent; }
.nav .active a{ color: #cd5d00; }
```

这里补充说明下，之所以小三角图标不使用图片，主要是本着一个原则：能用样式控制的就不用图片。

## flash切割

从 PSD 来看，flash 模块只是一张全屏的广告图，所以只要把广告图保存下来，写入到页面中即可。

对应的 HTML 代码：

```
<div class="flash">
    <img src="pic/banner.jpg" alt="" width="1400" height="339">
</div>
```

CSS 书写分析：

* flash 模块的背景色为广告的背景色的延展，并且高度为图片的图片；

* 图片需要居中显示；


对应的 CSS 代码：

```
/*------------ flash ------------*/
.flash{ height: 339px; background-color: #ffced4; text-align: center;}
```

## sidebar切割

### 结构分析

![](/assets/sidebar_bg1.jpg)

由 PSD 可以看出，sidebar 可以分为 sidebar\_title 和 sidebar\_con 两大部分组成。

对应的HTML代码：

```
<div class="sidebar">
    <h3 class="sidebar-title">课程分类</h3>
    <ul class="sidebar-con"></ul>
</div>
```

### sidebar-title 分析

sidebar-title 背景图片是渐变的，并且文字具有阴影效果，鉴于此，我们这边直接将其切为图片（原则上：文字是不跟背景连在一起切的），即便如此，文字说明我们也不能省略。另外，既然是标题，那么我们就使用 h 标签来定义

对应的 HTML 代码

```
<h3 class="sidebar-title">课程分类</h3>
```

CSS 书写分析：

由于我们已经将标题跟背景切在一张图里，那么在样式上，我们就应该控制将我们定义的文字隐藏起来，不在浏览器中显示。

对应的 CSS 代码：

```
.sidebar-title{ height: 60px; background: url(../image/bg-title.png) no-repeat 0 0; text-indent: -999em; overflow: hidden;}
```

### sidebar-con 分析

![](/assets/sidebar_con_bg1.jpg)

sidebar-con 由4个 &lt;li&gt; 构成，并且 &lt;li&gt; 打开项背景图片为白色，并且有一个向右的小三角。

对应的HTML代码：

```
<ul class="sidebar-con">
    <li>
        <a href="#" title="">女职工操作手册</a>
    </li>
    <li class="active">
        <a href="#" title="">女职工操作手册</a>
    </li>
    <li>
        <a href="#" title="">女职工操作手册</a>
    </li>
    <li>
        <a href="#" title="">女职工操作手册</a>
    </li>
</ul>
```

CSS 书写分析：

侧边选项打开项的小三角的处理跟导航上小三角的处理一样，就不多说了。

这里还需要注意的是边框的处理，列表项打开状态时，上下左右各有边框，为了鼠标经过选项时，不出现过多的抖动，在默认状态时，也会设置一个边框，只不过跟背景颜色一致，视觉上好像没有边框。

对应的 CSS 代码：

```
.sidebar-con{ background-color: #fbeeda; border-bottom: 1px solid #f3d2a1;}
.sidebar-con li{ height: 48px; line-height: 48px; }
.sidebar-con li a{ position: relative; display: block; padding-left: 24px; border-style:solid; border-width: 1px; border-color: #fbeeda #f3d2a1 #fbeeda #f3d2a1;}
.sidebar-con .active a,
.sidebar-con li a:hover{ background-color: #fff; border-color: #f3d2a1 #fff #f3d2a1 #fe5d00; border-left-width: 2px;}
.sidebar-con .active a:after,
.sidebar-con li a:hover:after{ content: ""; display: block; position: absolute; top: 20px; left: 0; width: 0; height: 0; border-style:solid; border-width: 4px; border-color: transparent transparent transparent #fe5d00; }
```

## main切割

### 结构分析

![](/assets/main_bg1.jpg)

由 PSD 可以看出 main 可以由上半部分的 main-title 和下半部分的 main-con 两部分组成。

对应的HTML代码：

```
<div class="main">
    <h3 class="main-title">女职工安全规范</h3>
    <div class="main-con"></div>
</div>
```

### main-title 分析

main-title 文字为24px、微软雅黑，底部边框为渐变过渡色，因此这部分我们将其切为图片，作为背景处理。

对应的CSS代码：

```
.main-title{ padding: 0 0 8px 4px; background: url(../image/line.png) no-repeat bottom center; font-size: 24px; font-family: "Microsoft YaHei"; line-height: 1;}
```

### main-con 分析

![](/assets/main_con1.jpg)

main-con由上半部分的列表 main-list 和下半部分的分页 main-page 两个部分组成。

对应的 HTML 代码：

```
<div class="main-con">
    <ul class="main-list"></ul>
    <div class="main-page"></div>
</div>
```

**main-list 分析**

![](/assets/main_list1.jpg)

