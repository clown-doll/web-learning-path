# 函数

Sass 提供了很多函数可供使用，最常用的应该是颜色函数。

颜色函数中，常用的是：

* `lighten($color, $amount)` 通过改变颜色的亮度值，让颜色变亮

* `darken($color, $amount)` 通过改变颜色的亮度值，让颜色变暗

* `saturate($color, $amount)` 通过改变颜色的饱和度，让颜色更饱和

* `desaturate($color, $amount)` 通过改变颜色的饱和度，让颜色更少的饱和

* `grayscale($color)` 将一个颜色变成灰色


更多 Sass 内置函数，可以去查看 [Sass Functions](http://www.cat7.cn/2016/01/08/sass/)。

## 自定义函数

Sass 中还拥有自定义函数的功能，通过 `@function` 来定义。它就像 javascript 里面的函数一样，返回的是一个值，而不是一段 CSS 样式。

```
@function double($n){
    @return $n * 2;
}
 
#sidebar{
    width: double(5px);
}
```

解析结果：

```
#sidebar {
    width: 10px;
}
```

