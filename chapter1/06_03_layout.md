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

对应前面主体结构的样式代码：

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

### 主体结构分析

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

logo 这块主要由两部分组成：

* logo 图片：由于 logo 不经常替换，所以这部分可以作为背景图片处理

* 站点文字：分为上下两部分，项目名称及站点名称


对应 HTML 代码：





