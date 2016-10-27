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

## 链接



