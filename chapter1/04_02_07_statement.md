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



