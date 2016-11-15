# 页面布局

经过前面对 PSD 的分析，我们就可以开始正式切割页面了。

### 搭建框架

根据前面的分析，这个页面主体结构如下：

![](/assets/full_psd2.jpg)

按照划分的5个区域，书写对应的 HTML 代码：

```
<!-- header -->
<div class="header"></div>
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

