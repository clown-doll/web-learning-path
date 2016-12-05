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

### switch 语句

switch 语句与 if 语句类似，都是多分支判断语句。其语法如下：

```
switch (expression) {
    case value: 
        statement
        break;
    case value: 
        statement 
        break;
    ...
    default: statement
}
```

switch 语句中的每一种情形（`case`）的含义是：如果表达式等于这个值（`value`），则执行后面的语句（`statement`）。而 `break` 关键字用于跳出 `switch` 语句，及执行完当前分支则跳出循环语句。如果省略 `break`，会导致执行完当前的 `case` 后，继续执行下一个 `case`，直到遇到 `break` 或者语句结束。最后的 `default` 关键字用于当表达式的值不匹配前面任何一个 `case`，则执行 `default` 后面的 `statement`。

我们一起看一个例子：

```
switch (i) {
    case 25:
        console.log("25");
        break;
    case 35:
        console.log("35");
        break;
    case 45:
        console.log("45");
        break;
    default:
        console.log("other!");
}
```

我们一起回忆下，如果用 if 语句，应该怎么写上面的代码呢？

```
if (i == 25) {
    console.log("25");
} else if (i == 35) {
    console.log("35");
} else if (i == 45) {
    console.log("45");
} else {
    console.log("other!");
}
```

看上面的代码，写了一堆的 if else 语句。为了避免出现这种情况，我们通常规定，当判断分支大于等于 3 的情况，我们就使用 switch 语句来控制。

当多个 case 执行的代码一样的情况下，我们可以将其合并处理，如下：

```
switch (i) {
    case 25:
    case 35:
        console.log("25 或 35");
        break;
    case 45:
        console.log("45");
        break;
    default:
        console.log("other!");
}
```

上面的例子，`case 25` 和 `case 35` 将同样执行 `console.log("25 或 35");`

## 循环语句

### while 语句

while 语句会先判断条件，条件为真则执行代码；条件为假，则永远不执行代码。它属于前测试循环语句。其语法如下：

```
while (expression) 
    statement
```

下面是一个例子：

```
var i = 0;
while (i <10) {
    console.log(i);
    i += 2;
}
```

这个例子中，变量 `i` 初始值为 0，满足条件 `i < 10`，因此值被增加 2；此时 `i = 2` ，同样满足条件，因此值再被增加 2。以此类推，直到 `i >= 10` 循环才结束。在控制台中，分别会输出：0，2，4，6，8，10。

### do-while 语句

do-while 语句与 while 语句有所区别。它是一种后测试循环语句，即只有在循环体代码执行之后，才会测试判断条件。也就是说，在对条件求值之前，循环体的代码至少会被执行过一次。其语法如下：

```
do {
    statement
} while (expression);
```

也一起看一个例子：

```
var i = 0;
do {
    console.log(i);
    i += 2;
} while (i < 10);
```

判断过程跟上面一个例子一样，只不过，是先执行了循环体，再进行判断。

### for 语句

除了前面介绍的两种循环语句，还有一种更加方便的循环控制语句，即 for 语句。

for 语句也是一种前测试循环语句。它具有在执行循环之前初始化变量和定义循环后要执行的代码的能力。其语法如下：

```
for (initialization; expression; post-loop-expression) statement
```

看下面这个例子：

```
var count = 10;
for (var i = 0; i < count; i++) {
    console.log(i);
}
```

上面的代码定义了变量 `i`，其初始值为 0 。当条件表达式 `i < count` 返回 `true` 的情况下会进入 for 循环，每次将 `i` 值打印出来。还有一个需要注意的是，如果执行了循环体中的代码，那一定会对循环后的表达式 `i++` 进行求值，使变量 `i` 的值递增 1。

上面的例子，其实等同于下面的 while 语句：

```
var count = 10,
    i = 0;
while (i < 10) {
    console.log(i);
    i++;
}
```

还有必要指出的是，for 循环中的变量 i ，也可以在外部被定义，如下：

```
var count = 10, 
    i; 
for (i = 0; i < count; i++) {
    console.log(i);
}
```

同时，for 语句中的初始化表达式、控制表达式和循环后表达式都是可选的，我们甚至可以这样写：

```
for (;;) { 
    console.log(1); 
}
```

上面的代码，由于没有任何限制条件，就成了无限循环了。

### for\/in 语句

for\/in 语句用来枚举对象的属性。其语法如下：

```
for (variable in object) 
    statement
```

看下面的例子：

```
for (var prop in window) {
    console.log(prop);
}
```

这个例子使用 for\/in 循环打印了 BOM 中 `window` 对象的所有属性（BOM 在后续课程中会学习）。每次执行循环时，都会将 `window` 对象中存在的一个属性名赋值给变量 `prop`。这个过程会一直持续到对象中的所有属性都被枚举一遍为止。

在执行 for\/in 语句的过程中，JavaScript 解析器会首先计算 `object` 表达式。如果表达式为 `null` 或 `undefined` ，JavaScript 解析器会跳过循环并执行后续的代码。在 ES5 前，这种情况会报错。为了保证最大限度的兼容性，建议在使用 for\/in 循环之前，先检测确认该对象的值不是 `null` 或 `undefined`。

## 跳转语句

跳转语句可以使得 JavaScript 执行从一个位置跳转到另一个位置。

### break 语句

前面在 switch 语句中，我们已经有接触过 break 语句。其语法即：

```
break;
```

在循环中，不管是出于什么原因，只要**不想继续执行整个循环**，都可以用 break 语句提前退出。

看下面的例子：

```
for (var i = 0; i < 10; i++) {
    console.log(i);
    if ( i == 5) {
        break;
    }
}
```

上面的代码，只会打印出0，1，2，3，4，5 。因为当 `i` 为 5 的时候，使用了 `break` 语句，它会跳出整个循环，使循环终止。

### continue 语句

continue 语句与 break 语句很相似，但是不同的是，它不是退出循环，而是跳出当前循环、转而执行下一次循环。其语法为：

```
continue;
```

我们一起看一个例子：

```
var num = 0;

for (var i = 1; i < 10; i++) {
    if (i % 5 == 0) {
        continue;
    }
    num++;
}

console.log(num); // 8
```

例子的结果显示 8，也就是循环总共执行了 8 次。当变量 `i` 等于 5 时，循环会在 `num` 再次递增之前退出，但接下来执行的是下一次循环，即i的值等于 6 的循环。于是，循环又继续执行，直到 i 等于 10 时自然结束。而 `num` 的最终值之所以是 8，是因为 continue 语句导致它少递增了一次。

### return 语句

return 语句是制定函数调用后的返回值。其语法为：

```
return expression;
```

return 语句只能在函数体内出现。

当函数执行到 return 语句时，会终止执行，并返回 `expression` 的值供调用。如下面的例子：

```
function square(x) {
    return x*x; 
} 
square(2);  // 结果将为 4 （2*2 = 4） 
```

如果函数没有 return 语句，将执行到最后一条语句，然后结束，函数最终返回 undefined 。

return 语句也可以单独使用，不带 `expression` ，这样的话，函数最终也是返回 undefined。

### throw 语句

throw 语句用于将程序运行时产生的错误显示抛出。其语法是：

```
throw expression;
```

expression 的值可以是任意类型的。也可以是一个 Error 对象，这个对象是 JavaScript 内置对象，有一个 name 属性表示错误类型，一个 message 属性存储传递给构造函数的字符串。看下面的例子：

```
function factorial(x) {
    // 如果输入参数是非法的，则抛出一个异常
    if (x < 0) throw new Error("x不能是负数");
    // 否则，计算出一个值，并正常地返回它
    for (var f = 1; x > 1; f *= x, x--) /* empty */;
    return f;
}
```



