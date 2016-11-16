# 页面布局

经过前面对 PSD 的分析，我们就可以开始正式切割页面了。

### 搭建框架

根据前面的分析，这个页面主体结构如下：

![](/assets/full_psd2.jpg)

按照划分的5个区域，书写对应的 HTML 代码：

```
<!-- header -->
<div class="header">
    <div class="wrapper">

    </div>
</div>
<!-- /header -->
<!-- banner -->
<div class="banner"></div>
<!-- /banner -->

<!-- container -->
<div class="container">
    <div class="sidebar"></div>
    <div class="main"></div>
</div>
<!-- /container -->

<!-- footer -->
<div class="footer"></div>
<!-- /footer -->
```

在 header 里面定义了一个名为 wrapper 的样式，是因为头部主体内容在 960px 内，我们用这个限制内容分布。

对应前面主体结构的样式代码：



