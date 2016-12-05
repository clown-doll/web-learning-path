# 语句

表达式是短语，语句是整句或者命令，用来执行以使某件事情发生。

## 表达式语句

表达式语句是最简单的原句，如赋值语句：

```
var name = cat;
var greeting = "Hello" + name;
```

递增递减、delete 运算、函数调用等都是表达式语句。

## 复合语句和空语句

将多条语句联合在一起，就形成一条复合语句，可以用花括号将多条语句括起来，如：

```
{
    x = Math.PI;
    cx = Math.cos(x);
    console.log(cx);
}
```

空语句即包含 0 条语句的语句，如下：

```
;
```

在 for 循环中，我们会用到空语句，后面我们再具体讲。

## 声明语句

`var` 和 `function` 都是声明语句，它们分别用来声明变量和函数。

### var

前面其实都有介绍过了，用 `var` 可以声明一个或多个变量，如下：

```
var a;  // 声明一个简单变量
var b = 1;  // 声明一个带有初始值的变量
var c, d;  // 同时声明两个变量
```

### function

`function` 用来定义函数。如：

```
function hypotenuse(x, y) {
    return Math.sqrt(x*x + y*y);
}
```

## 条件语句

条件语句是通过判断指定表达式的值来决定执行还是跳过某些语句。条件预计主要有：`if`、`else if` 和 `switch`。

### if 语句

if 语句是最常用的一个语句，其语法如下：

```
if (condition) statement1 else statement2
```

其中 `condition` 是任意表达式，为判断语句的条件。如果对 `condition` 求值结果为 `true`，则执行 `statement1` ，如果对 `condition` 求值结果为 `false` ，则执行 `statement2` 。

一起来看一个例子：

```
if (age > 18) {
    console.log("成年了！");
} else {
    console.log("未成年！");
}
```

其实，if 语句可以单独使用，不一定跟 else 语句同时出现：

```
if (age > 18) {
    console.log("成年了！");
}
```

另外，还可以像这样使用多分支 if 语句：

```
if (age > 20) {
    console.log("年龄大于20！");
} else if (age < 10) {
    console.log("年龄小于10！");
} else {
    console.log("年龄介于20跟10之间！");
}
```





