# 判断及循环语句

## @if判断

`@if` 用于条件判断，可一个条件单独使用，也可以和 `@else` 结合多条件使用：

```
p{
    @if 1+1==2 {border:1px solid;}
    @if 5<3 {border:2px dotted;}
}
```

解析结果：

```
p {
    border: 1px solid;
}
```

## 条件判断

语法为：`if($condition, $if_true, $if_false)`

三个参数分别表示：条件，条件为真的值，条件为假的值。

```
$isBgDark: true;
.box {
    color: if($isBgDark, #fff, #000);
}
```

解析结果：

```
.box {
    color: #fff;
}
```

## for循环

for循环有两种语法：`@for $var from start through end` 和 `@for $var from start to end`。`$i` 表示变量，`start` 表示起始值，`end` 表示结束值，这两个的区别是关键字 `through` 表示包括 `end` 这个数，而 `to` 则不包括 `end` 这个数。

**使用关键字 to**

```
@for $i from 1 to 3{
    .border-#{$i} {
        border: #{$i}px solid blue;
    }
}
```

解析结果：

```
.border-1 {
    border: 1px solid blue;
}
 
.border-2 {
    border: 2px solid blue;
}
```

**使用关键字 through**

```
@for $i from 1 through 3{
    .border-#{$i} {
        border: #{$i}px solid blue;
    }
}
```

解析结果：

```
.border-1 {
    border: 1px solid blue;
}
 
.border-2 {
    border: 2px solid blue;
}
 
.border-3 {
    border: 3px solid blue;
}
```

## while循环

```
$i: 4;
@while $i > 0 {
    .item-#{$i} { width: 2em * $i; }
    $i: $i - 2;
}
```

解析结果：

```
.item-4 {
    width: 8em;
}
 
.item-2 {
    width: 4em;
}
```

## each循环

语法为：`@each $var in`。表示循环一个列表里面所有的值，并执行相应的代码。

```
@each $member in a, b, c{
    .#{$member} {
        background-image: url('/image/#{$member}.jpg');
    }
}
```

解析结果：

```
.a {
    background-image: url("/image/a.jpg");
}
 
.b {
    background-image: url("/image/b.jpg");
}
 
.c {
    background-image: url("/image/c.jpg");
}
```

