# 格式化排版

## 文字排版

文字排版涉及到文字大小，颜色，字体等。

### 字体

CSS 中使用 `font-family` 属性来设置文字的字体。

```
.family1 { font-family: "Microsoft YaHei"; }
.family2 { font-family: SimSun; }
```

![](/assets/css-typeset-font-family.png)

上面两种字体的定义，也都可以用中文来设置：`font-family: "微软雅黑";` ， `font-family: "宋体";` 。不过，我们建议都用字体的英文名来定义，兼容性更好。这里有一份[CSS字体中英文对照表](http://www.cat7.cn/2016/04/19/css%E5%AD%97%E4%BD%93%E4%B8%AD%E8%8B%B1%E6%96%87%E5%AF%B9%E7%85%A7%E8%A1%A8/)，大家可以对照着查看。

注意：不要设置不常用的字体，因为如果用户本地电脑上如果没有安装你设置的字体，就会显示浏览器默认的字体。

当然，我们可以为所需的文字设置更多的字体，解析时会根据字体定义的顺序依次去判断用户本地是否有该字体，如果没有则选择后面一个定义的字体，如果全部都没有，就显示浏览器默认的字体。

多个字体直接用英文逗号（ , ）隔开，另外还需要注意的是，当一个字体有多个单词或是中文时，需要用双引号将其包在一起。

```
p { font-family: "Segoe UI", "Lucida Grande", Helvetica, Arial, "Microsoft YaHei" sans-serif; }
```

### 字号及颜色

CSS 中使用 font-size 属性来设置文字字号。

```
.font14 { font-size: 14px; }
.font16 { font-size: 16px; }
.font18 { font-size: 18px; }
.font20 { font-size: 20px; }
```

![](/assets/css-typeset-font-size.png)

CSS 字体颜色的设置，我们在前面的例子中已经用过很多次了，即用 color 属性来设置。

```
.red { color: red; }
.grey { color: #999; }
```

![](/assets/css-typeset-font-color.png)

### 文字粗细

可以用 `font-weight` 属性来设置文本的粗细。

```
h2 { font-weight: normal; }
p { font-weight: bold; }
```

![](/assets/css-typeset-font-weight.png)

`h2` 默认是加粗的，设置为 `normal` 值后则不再加粗，`p` 默认不加粗，设置 `bold` 后则显示为加粗。

`font-weight` 属性的可选值有：

* `normal`：默认值，标准字符。

* `bold`：粗体字符。

* `bolder`：更粗的字符。

* `lighter`：更细的字符。

* 数值（`100, 200 ... 900`）：有数字控制粗细。`400` 相当于 `normal`，`700` 等同于 `bold` 。


### 字体风格

使用 `font-style` 属性来定义字体风格，即文字是显示为正常字体，还是倾斜或者斜体。

```
.normal { font-style: normal; }
.italic { font-style: italic; }
.oblique { font-style: oblique; }
```

![](/assets/css-typeset-font-stylet.png)

如上例所示， `font-style` 属性有三个常见取值：

* `normal`： 标准的字体样式

* `italic`： 斜体的字体样式

* `oblique`： 倾斜的字体样式


### 文本修饰

有时候我们可能需要将文本设置为由下划线或中划线等样式，CSS 中可以用 `text-decoration` 属性来定义。

常见的取值有：

* `none`：为默认值。无修饰。

* `underline`：文本下的一条线。

* `overline`：文本上的一条线。

* `line-through`： 穿过文本的一条线。


```
.overline { text-decoration: overline; }
.through { text-decoration: line-through; }
.underline { text-decoration: underline; }
```

![](/assets/css-typeset-text-decoration.png)

## 段落排版

段落排版主要是控制段落的缩进、行间距，对齐等。

### 缩进

`text-indent` 属性用于规定文本块中首行文本的缩进。

```
p { text-decoration: 2em; }
```

通常情况下，我们会控制段落首行缩进两个文字大小，如上例所设置的。

另外，`text-indent` 运行设置负值，如果设置了负值，文本将往左偏移

我们一起来看下 `text-index` 在浏览器中的显示效果：

![](/assets/css-typeset-text-indent.png)

### 行间距

`line-height` 属性用于设置文本行间的距离（行高）。

```
.lineheight { line-height: 2; }
.lineheight2 { line-height: 40px; }
```

![](/assets/css-typeset-line-height.png)

如上例所示，line-height 属性的取值可以是数字，也可以是固定的尺寸或者百分比。

* 数字 ：此数字会与当前的字体尺寸相乘来设置行间距。

* 百分比：基于当前字体尺寸的百分比设置行间距。

* 固定尺寸：通常是带单位的固定尺寸，如 20px 等。


### 中文字间距、字母间距

如果想在网页排版中设置文字间隔或者字母间隔就可以使用 `letter-spacing` 属性来定义。

如果想控制英文单词直接的间距，可以使用 `word-spacing` 属性来定义。

```
.letter { letter-spacing: 15px; }
.word { word-spacing: 30px; }
```

![](/assets/css-typeset-letter_word_space.png)

### 文本对齐

段落排版中，还有一个比较常用到的属性 `text-align` ，用于定义文本水平方向的对齐方式。

有以下几种对齐方式：

* `left`：左对齐

* `right`：右对齐

* `center`：居中对齐

* `justify`：两端对齐


```
.left { text-align: left; }
.right { text-align: right; }
.center { text-align: center; }
.justify {  
    text-align:justify;
    text-justify:distribute-all-lines;/*ie6-8*/
    text-align-last:justify;/* ie9*/
    -moz-text-align-last:justify;/*ff*/
    -webkit-text-align-last:justify;/*chrome 20+*/
}
```

![](/assets/css-typeset-text_align.png)

大家可能会好奇，为什么两端对齐的代码有那么长一串。这是为了设置各个浏览器的兼容性。 `text-justify` 在各个浏览器的支持情况不一样，因此，为了让主流浏览器都显示出我们想要的效果，需要针对每个浏览器进行特殊设置。关于浏览器兼容性的问题，我们后续会专门讲解。

## 背景

CSS 中允许纯色作为背景，也允许使用图片作为背景。

### 背景色

CSS 中使用 `background-color` 属性为元素设置背景色。这个属性接受任何合法的颜色值。

```
body { background-color: #999; }
```

可以为所有元素都设置背景色，其默认值是  `transparent` ，即透明。

### 背景图片

想要图像当作背景，需要使用 `background-image` 属性。 其默认值是 `none`，及背景上没有放置任何图像。

```
body { background-image: url(images/bg.gif); }
```

![](/assets/css-typeset-bg-image.png)

现在，我们网页的背景就变为用图像填充的了。

### 背景重复

上例中，我们的背景图片 `bg.gif` 是一张 150\*150 大小的图片，但是它却铺满了整个文档区域，这是为什么呢？

background-repeat 属性在控制这一切。默认情况下，它的取值是 `repeat`，即水平方向和垂直方向都重复背景。效果就如上例所示。它还有另外几个常见的取值：

* `repeat-x`：背景图像在水平方向重复。

* `repeat-y`：背景图像在垂直方向重复。

* `no-repeat`：背景图像不重复。


```
.repeat { background-repeat: repeat; }
.repeat-x { background-repeat: repeat-x; }
.repeat-y { background-repeat: repeat-y; }
.no-repeat { background-repeat: no-repeat; }
```

![](/assets/css-typeset-bg-image-repeat.png)

### 背景定位

我们还可以控制，图片在背景中的显示位置。这需要使用 `background-position` 属性。

`background-position` 属性提供值有多种方法。

**关键字**

关键字定义位置很好理解，即利用 top，bottom，left，right 和 center 来定义位置。

关键字一般成对出现，表示水平方向和垂直方向。如果只写了一个关键字，那么另一个关键字默认为 center。

```
.center { background-position: center; }
.top { background-position: top; }
.bottom { background-position: bottom; }
.right { background-position: right; }
.left { background-position: left; }
```

![](/assets/css-typeset-bg-image-position.png)

**百分数值**

百分数值的表现方式会相对复杂些，它同时应用于元素和图像，即图像本身\(x%, y%\)的那个点，与背景区域的\(x%, y%\)的那个点重合。比如

```
body { background-position: 50% 50%; }
```

这样设置后，背景图像会居中显示，图像的中心点\(50%, 50%\)与元素的中心点\(50%, 50%\)对齐。

再来看个例子，深入理解下：

```
.per { background-position: 20% 30%; }
```

![](/assets/css_typeset_background_position_per.png)

我们背景图是 150\*150 的，那么它的 \(20%, 30%\) 的点在 \(30px, 45px\) 的位置；我们背景区域是 200\*200，它的 \(20%, 30%\) 的点在 \(40, 60\) ，两个点对齐，最终背景图片就像上图那样呈现了。

**长度值**

长度值解释的是元素内边距区左上角的偏移。偏移点是图像的左上角。

```
.px { background-position: 10px 10px; }
```

![](/assets/css_typeset_background_position_px.png)

如上图所示，图像左上角距离元素左上角的偏移为 \(10px, 10px\) 时，即为上图呈现的效果。

### 背景关联

如果文档比较长，那么当文档向下滚动时，背景图像也会随之滚动。当文档滚动到超过图像的位置时，图像就会消失。`background-attachment` 属性可以设置背景图像是否固定或者随着页面的其余部分滚动。

常见的取值有：

* `scroll`：默认值。背景图像会随着页面其余部分的滚动而移动。

* `fixed`： 当页面的其余部分滚动时，背景图像不会移动。


### 背景的简写属性

我们可以把以上背景属性合在一起定义，而不用每次都单独写出来。

如：

```
background-color: #f5f5f5;
background-image: url(images/bg.gif);
background-position: center;
background-repeat: no-repeat;
background-attachment: scroll;
```

以上这些属性，都可以合并起来一起写：

```
background: #f5f5f5 url(images/bg.gif) center scroll no-repeat;
```

而且，不需要每个值都指定。如果省略值得化，会自动使用默认值。如，上面的代码，其实与下面是等价的：

```
background: #f5f5f5 url(images/bg.gif) center no-repeat;
```



