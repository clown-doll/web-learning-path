# 变量

Sass 引入了变量的概念，可以将反复使用的属性值定义成变量，然后通过变量名来引用它们。

Sass 变量的声明跟 CSS 属性的声明很像，它使用 `$` 符号来标识，后面紧跟变量名，变量值和变量名之间用冒号 `:` 分隔开：

```
$height: 5em;
```

这时变量还没有生效，需要在 CSS 规则块内引用它：

```
$height: 5em;
div {
    height: $height;
}
```

解析结果：

```
div {
    height: 5em;
}
```

## 默认变量

在 Sass 变量值后面添加 `!default` 表示该值为变量的默认值。即如果这个变量被声明赋值了，那就用它声明的值，否则就用默认值。

经常有同学觉得 `!default` 并没有什么卵用，好像有没有 `!default` 都没有什么差别。

下面我们一起来看个例子，就会明白其中的差别了：

**未使用 !default**

```
$height: 5em;
$height: 10em;
div {
    height: $height;
}
```

解析结果：

```
div {
   height: 10em;
}
```

**使用 !default**

```
$height: 5em;
$height: 10em !default;
div {
    height: $height; 
}
```

解析结果：

```
div {
    height: 5em;
}
```

大家可以自己去编译下看看，结果会跟上面展示的是一样的。由此可见，有无使用 `!default` 还是有差别的。我们都知道 Sass 编译 CSS 是从上到下的，后面会覆盖前面的，所以第一段无 `!default` 的解析结果为 `10em` ，而第二段代码由于设置了 `!default` ，打破了这个规则，使用了前面定义的 `5em` ，因此解析出来的结果为： `5em` 。

那为什么很多同学都觉得有没有设置 `!default` 都一样呢？**是因为他们犯了个错误：先申明!default：**

```
$height: 10em !default;
$height: 5em;
 
div {
    height: $height; 
}
```

解析结果：

```
div {
    height: 5em;
}
```

说错误也不能算是错误，只是这样的写法，其实**跟按顺序覆盖写法是一致的，就完全没有必要设置 !default。**

综上所述，给出 `!default` 的两个正确应用场景：

```
//第一种，使用默认值 
//变量申明带有!default，但是之前没有这个变量的申明 
$height: 10em !default;
div {
    height: $height; 
}
 
//第二种，变量申明带有!default，但是前面还有这个变量的申明
$height: 5em;
$height: 10em !default;
div {
    height: $height;
}
```

## 特殊变量

如果变量用在属性名、选择器或者某些特殊情况下，则必须要用 `#{}` 包裹起来。

```
$border-direction: top; 
$font-size: 12px;
$lineheight: 1.5;
 
//应用于class和属性
.border-#{$border-direction}{
    border-#{$border-direction}: 1px solid #ccc;
}
//应用于复杂的属性值
body{
    font:#{$font-size}/#{$lineheight};
}
```

解析结果：

```
.border-top {
    border-top: 1px solid #ccc;
}
 
body {
    font: 12px / 1.5;
}
```

## 多值变量

多值变量分为 list 类型和 map 类型，简单来说 list 类型有点像 javascript 中的数组，而 map 类型有点像 javascript 中的对象。

### list数据

list 数据可通过空格，逗号或小括号分隔多个值：

```
//一维数据
$px: 5px 10px 20px 30px;
 
//二维数据，相当于javascript中的二维数组
$px: 5px 10px, 20px 30px;
$px: (5px 10px) (20px 30px);
```

list 数据可用 `nth($var,$index)` 取值：

```
$link-color: #08c #333; //第一个值为默认值，第二个鼠标滑过值
a{
    color:nth($link-color, 1);
    &:hover{
        color:nth($link-color, 2);
    }
}
```

解析结果：

```
a {
    color: #08c;
}
 
a:hover {
    color: #333;
}
```

关于 list 数据操作还有很多其他函数如 `length($list)`，`join($list1,$list2,[$separator])`，`append($list,$value,[$separator])`等，具体可参考 [List Functions](http://sass-lang.com/documentation/Sass/Script/Functions.html#list-functions)。

### map数据

map 数据 以 key 和 value 成对出现，其中 value 又可以是 list。

其格式为：`$map: (key1: value1, key2: value2, key3: value3);`

```
$heading: (h1: 2em, h2: 1.5em, h3: 1.2em);
```

map 数据 可通过 `map-get($map,$key)` 取值：

```
$headings: (h1: 2em, h2: 1.5em, h3: 1.2em);
@each $header, $size in $headings {
    #{$header} {
        font-size: $size;
    }
}
```

解析结果：

```
h1 {
    font-size: 2em;
}
 
h2 {
    font-size: 1.5em;
}
 
h3 {
    font-size: 1.2em;
}
```

关于 map 数据 还有很多其他函数如 `map-merge($map1,$map2)`，`map-keys($map)`，`map-values($map)` 等，具体可参考 [Map Functions](http://sass-lang.com/documentation/Sass/Script/Functions.html#map-functions)。

## 变量后面加…

`@mixin` （后面会提到）可以传多个参数，参数是以逗号 , 来分隔的，但是 CSS3 的一些属性可以设置多个值，并且每个值之间也是以逗号 , 来分隔的。这时候，`@mixin` 用逗号传参将出现问题。

这种情况下，在变量后面添加 `...` 就派上大用场了。

```
@mixin box-shadow($shadow...){
    -webkit-box-shadow:$shadow;
    -moz-box-shadow:$shadow;
    box-shadow:$shadow;
}
 
.box{
  @include box-shadow(0 0 5px 3px rgba(255, 0, 0, .6), 
                      0 0 5px 6px rgba(0, 182, 0, .6), 
                      0 0 5px 10px rgba(255, 255, 0, .6));
}
```

解析结果：

```
.box {
    -webkit-box-shadow: 0 0 5px 3px rgba(255, 0, 0, 0.6), 0 0 5px 6px rgba(0, 182, 0, 0.6), 0 0 5px 10px rgba(255, 255, 0, 0.6);
    -moz-box-shadow: 0 0 5px 3px rgba(255, 0, 0, 0.6), 0 0 5px 6px rgba(0, 182, 0, 0.6), 0 0 5px 10px rgba(255, 255, 0, 0.6);
    box-shadow: 0 0 5px 3px rgba(255, 0, 0, 0.6), 0 0 5px 6px rgba(0, 182, 0, 0.6), 0 0 5px 10px rgba(255, 255, 0, 0.6);
}
```

