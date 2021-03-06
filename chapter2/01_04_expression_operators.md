# 表达式和运算符

表达式即 JavaScript 中的个短语。常量、变量名、函数调用等都是表达式。

将简单表达式组合成复杂表达式最常用的方法就是使用运算符。

接下来，我们主要就是讲解 JavaScript 表达式和运算符的相关知识。

## 表达式

最简单的表达式就是“原始表达式”，它是表达式的最小单元。JavaScript 中的原始表达式包括：常量、直接量、关键字和变量，如

```
"hello world"   // 字符串
123             // 数字
1.2             // 小数
true            // 布尔值
false           // 布尔值
null            // 空
```

对象、数组的初始化表达式，如：

```
{ name: 'stone', age: 20}       // 对象
[ 1, 2, 3, 4, 5, 6, 7, 8 ]      // 数组
```

函数定义表达式，也可以称为”函数直接量“，如

```
function(){ console.log('good'); }    // 函数
```

属性访问表达式，运算结果是得到一个对象属性或数组元素值，如：

```
var o = {x:1, y:{z:3}};
var a = [0, 4];

o.y.z // 表达式o.y的z属性
o["x"] // 表达式o的x属性
a[1] // 表达式a中索引为1的元素
```

调用表达式即调用或执行函数的语法表示，如：

```
Math.max(x, y, z) // Math.max是一个函数，x, y, z是参数
```

对象创建表达式是创建一个对象并调用构造函数初始化新对象的属性，如：

```
new Object();
```

## 运算符

运算符用于算术表达式、比较表达式、逻辑表达式、赋值表达式等。大多数运算符都是由标点符合表示的，如"="。另一部分则由关键字表示，如"delete"。

### 优先级

运算符的优先级决定了表达式中运算执行的先后顺序，优先级高的运算符最先被执行。

先来看一个简单的例子：

```
3 + 5 * 4; // 23
```

由于乘法运算符比起加法运算符优先级更高，因此它会被最先执行，然后再执行加法，计算顺序是这样的：

```
5 * 4 = 20;
20 + 3 = 23;
```

**结合性**

结合性决定了拥有相同优先级的运算符的执行顺序。考虑下面这个表达式：

```
a OP b OP c  // OP表示操作符
```

左结合（从左到右计算），相当于把左边的子表达式加上小括号：

```
(a OP b) OP c
```

右结合（从右到左计算），相当于把右边的子表达式加上小括号：

```
a OP (b OP c)
```

**汇总表**

下面的表将所有运算符按照优先级的不同从高到低排列：

![](/assets/js-yxj.jpg)

### 一元运算符

只有一个操作数的运算符叫做一元运算符。

**递增递减运算符**

递增递减运算符分为：前置型（递增 `++i`，递减 `--i`）和后置型（递增 `i++`，递减 `i--`）。

前置型指的是自身先计算，再后赋值给变量；后置型指的是先将自身的值赋给变量，然后再自增1。我们来看个例子：

```
// 前置型
var i = 1;
console.log(i);  // 1
var a = ++i;
console.log(a);  // 2
console.log(i);  // 2

// 后置型
var b = i++;  
console.log(b);  // 2
console.log(i);  // 3
```

怎么理解这个例子呢？

我们先来看前置型部分。上面的例子相当于这样：

```
// 先自身加1，再赋值
var i = 1;
i = i + 1;
var a = i;
```

此时 i 已经为 2了，然后我们再看后置型部分，相当于：

```
// 此时 i = 2
// 先赋值，再自身加1
var b = i;
i = i + 1;
```

**一元加和一元减**

一元加即一个加号（`+`），本质上他对数组无任何影响，如：

```
var a = 10;
a = + a;
console.log(a);  // 20
```

但是，一元加对字符串却有作用，会把字符串转换成数字：

```
var a = "10";
console.log(typeof a);  // "string"
var b = +a;
console.log(typeof b);  // "number"
console.log(typeof a);  // "string"
```

上面那段代码将字符串 "10" 转换成了数字，它计算字符串的方式与 parseInt\(\) 类似。

注意，最后打印变量 a 的类型，还是 "string" ，这是由于字符串的特殊性，即它是不可变的，一旦创建就不能改变。

一元减即一个减号（`-`），其本质就是对数字求负值：

```
var a = 1;
a = -a;
console.log(a);  // -1
```

同样的，一元减也会把字符串转换成近似的数字，此外还会对其求负，如：

```
var a = "10";
console.log(typeof a);  // "string"
var b = - a;
console.log(typeof b);  // "number"
```

**delete**

`delete` 运算符用于删除对象属性或者数组元素，如果删除成功或所删除对象不存在，将返回true。如：

```
var o = {};
o.name = "cat";
console.log(o.name);  // "cat"
console.log(delete o.name);  // true
console.log(o.name);  // undefined 
console.log(delete o.age);  // true
```

注意，内置核心和客户端属性是不能被删除的。

**void**

`void` 运算符对任何值返回 undefined。该运算符的作用如下：

* 通过采用 `void 0` 取 `undefined` 比采用字面上的 `undefined` 更靠谱更安全，应该优先采用 `void 0` 这种方式。

* 填充 `<a>` 的 `href` 确保点击时不会产生页面跳转；填充`<image>` 的 `src`，确保不会向服务器发出垃圾请求。


如下面例子

```
console.log(typeof void 0);  // undefined
console.log(void 0);  // undefined

<a href="javascript:void(0)">test</a>;
```

### 乘性操作符

乘性操作符有 3 个：乘法、除法和求模。

**乘法**

乘法运算符由星号（`*`）表示。乘法操作符遵循以下规则：

* 如果操作数都是数值，执行常规的乘法计算，即两个正数或两个负数相乘的结果还是正数，而如果只有一个操作数有符号，那么结果就是负数。如果乘积超过了 JavaScript 数值的表示范围，则返回 Infinity 或 -Infinity；

* 如果有一个操作数是 NaN，则结果是 NaN；

* 如果是 Infinity 与 0 相乘，则结果是 NaN；

* 如果是 Infinity 与非 0 数值相乘，则结果是 Infinity 或 -Infinity，取决于有符号操作数的符号；

* 如果是 Infinity 与 Infinity 相乘，则结果是 Infinity； 如果有一个操作数不是数值，则在后台调用 Number\(\)将其转换为数值，然后再应用上面的规则。


**除法**

除法运算符由斜线（`/`）表示。除法操作符遵循以下规则：

* 如果操作数都是数值，执行常规的除法计算，即两个正数或两个负数相除的结果还是正数，而如果只有一个操作数有符号，那么结果就是负数。如果商超过了 JavaScript 数值的表示范围，则返回 Infinity 或 -Infinity；

* 如果有一个操作数是 NaN，则结果是 NaN；

* 如果是 Infinity 被 Infinity 除，则结果是 NaN；

* 如果是零被零除，则结果是 NaN；

* 如果是非零的有限数被零除，则结果是 Infinity 或 -Infinity，取决于有符号操作数的符号；

* 如果是 Infinity 被任何非零数值除，则结果是 Infinity 或 -Infinity，取决于有符号操作数的符号；

* 如果有一个操作数不是数值，则在后台调用 Number\(\) 将其转换为数值，然后再应用上面的规则。


**求模运算符**

求模运算符由百分号（`%`）表示。求模操作符遵循以下规则：

* 如果操作数都是数值，执行常规的除法计算，返回除得的余数；

* 如果被除数是无穷大值而除数是有限大的数值，则结果是 NaN；

* 如果被除数是有限大的数值而除数是零，则结果是 NaN；

* 如果是 Infinity 被 Infinity 除，则结果是 NaN；

* 如果被除数是有限大的数值而除数是无穷大的数值，则结果是被除数；

* 如果被除数是零，则结果是零；

* 如果有一个操作数不是数值，则在后台调用 Number\(\) 将其转换为数值，然后再应用上面的规则。


### 加性操作符

加性操作符包括加法和减法。

**加法运算符**

如果两个运算符都是数值，执行常规的加法计算，然后根据下列规则返回结果：

* 如果有一个操作数是 NaN，则结果是 NaN；

* 如果是 Infinity 加 Infinity，则结果是 Infinity；

* 如果是 -Infinity 加 -Infinity，则结果是 -Infinity；

* 如果是 Infinity 加- Infinity，则结果是 NaN；

* 如果是 +0 加 +0，则结果是 +0；

* 如果是 -0 加 -0，则结果是 -0；

* 如果是 +0 加 -0，则结果是 +0；


如果有一个操作数不是数值，那么就要应用如下规则：

* 如果两个操作数都是字符串，则将第二个操作数与第一个操作数拼接起来；

* 如果只有一个操作数是字符串，则将另一个操作数转换为字符串，然后再将两个字符串拼接起来；

* 如果有一个操作数是对象、数值或布尔值，则调用它们的 toString\(\) 方法取得相应的字符串值，然后再应用前面关于字符串的规则。对于 undefined 和 null，则分别调用 String\(\) 函数并取得字符串 "undefined" 和 "null"；

* 如果是 null 加 null，则结果是 0；

* 如果是 undefined 加 undefined，则结果是 NaN；


来看下面例子

```
var result1 = 5 + 5;            // 两个数值相加
console.log(result1);           // 10

var result2 = 5 + "5";          // 一个数值和一个字符串相加
console.log(result2);           // "55"

var num1 = 5;
var num2 = 10;
var message = "The sum of 5 and 10 is " + num1 + num2;
console.log(message);   // "The sum of 5 and 10 is 510" 
```

**减法运算符**

如果两个运算符都是数值，执行常规的减法计算，然后根据下列规则返回结果：

* 如果有一个操作数是 NaN，则结果是 NaN；

* 如果是 Infinity 减 Infinity，则结果是 NaN；

* 如果是 -Infinity 减 -Infinity，则结果是 NaN；

* 如果是 Infinity 减 -Infinity，则结果是 Infinity；

* 如果是 -Infinity 减 Infinity，则结果是 -Infinity；

* 如果是 +0 减 +0，则结果是 +0；

* 如果是 +0 减 -0，则结果是 -0；

* 如果是 -0 减 -0，则结果是 +0；


如果有一个操作数不是数值，那么就要应用如下规则：

* 如果有一个操作数是字符串、布尔值、null 或 undefined，则先在后台调用 Number\(\) 函数将其转换为数值，然后再根据前面的规则执行减法计算。如果转换的结果是 NaN，则减法的结果就是 NaN；

* 如果有一个操作数是对象，则调用对象的 valueOf\(\) 方法以取得表示该对象的数值。如果得到的值是 NaN，则减法的结果就是 NaN。如果对象没有 valueOf\(\) 方法，则调用其 toString\(\)方法并将得到的字符串转换为数值。

* 如果是 null 减 null，则结果是 0；

* 如果是 undefined 减 undefined，则结果是 NaN；


来看下面例子

```
console.log(5 - true);  // 4，因为true被转换成了1
console.log(NaN - 1);  // NaN
console.log(5 - 3);  // 2
console.log(5 - "");  // 5，因为"" 被转换成了0
console.log(5 - "2");  // 3，因为"2"被转换成了2
console.log(5 - null);  // 5，因为null被转换成了0
```

### 关系操作符

关系操作符有：小于（`<`）、大于（`>`）、小于等于（`<=`）和大于等于（`>=`），它们都返回一个布尔值。

如果关系操作符遵循以下规则：

* 如果两个操作数都是数值，则执行数值比较。

* 如果两个操作数都是字符串，则比较两个字符串对应的字符编码值（可以通过字符串的 charCodeAt\(\) 函数获取字符编码值）。

* 如果一个操作数是数值，则将另一个操作数转换为一个数值，然后执行数值比较。

* 如果一个操作数是对象，则调用这个对象的 valueOf\(\) 方法，用得到的结果按照前面的规则执行比较。如果对象没有 valueOf\(\) 方法，则调用 toString\(\) 方法，并用得到的结果根据前面的规则执行比较。

* 如果一个操作数是布尔值，则先将其转换为数值，然后再执行比较。


来看下面例子

```
console.log("Brick" < "alphabet");  // true
console.log("brick" < "alphabet");  // false
console.log("23" < "3");  // true
console.log("23" < 3);  // false
console.log("a" < 3);  // false
console.log(NaN < 3);  // false
console.log(NaN >= 3);  // false
```

**in 运算符**

`in` 运算符希望它的左操作数是一个字符串或可以转换为字符串，希望它的右操作数是一个对象。如果右侧的对象拥有一个名为左操作数值的属性名，那么表达式返回 true，例如：

```
var point = { x:1, y:1 };  // 定义一个对象
console.log("x" in point);  // true，对象有一个名为"x"的属性
console.log("z" in point);  // false，对象中不存在名为"z"的属性
console.log("toString" in point);  // true，对象继承了toString()方法

var data = [7,8,9];  // 拥有三个元素的数组
console.log("0" in data);  // true，数组包含元素"0"
console.log(1 in data);  // true，数字转换为字符串
console.log(3 in data);  // false，没有索引为3的元素
```

**instanceof 运算符**

`instanceof` 运算符希望左操作数是一个对象，右操作数标识对象的构造函数。如果左侧的对象是右侧类的实例，则表达式返回 true；否则返回 false。比如：

```
var d = new Date();  // 通过 Date() 构造函数来创建一个新对象
console.log(d instanceof Date);  // true，d 是由 Date() 创建的
console.log(d instanceof Object);  // true，所有的对象都是 Object 的实例
console.log(d instanceof Number);  // false，d 不是一个 Number 对象

var a = [1, 2, 3];  // 通过数组字面量的写法创建一个数组
console.log(a instanceof Array);  // true，a 是一个数组
console.log(a instanceof Object);  // true，所有的数组都是对象
console.log(a instanceof RegExp);  // false，数组不是正则表达式
```

### 相等操作符

有两组操作符：相等和不相等（先转换再比较）；全等和不全等（仅比较不转换）。

**相等和不相等**

相等（`==`）和不相等（`!=`）在转换不同的数据类型时，遵循下列基本规则：

* 如果有一个操作数是布尔值，则在比较相等性之前先将其转换为数值（false 转换为 0，而 true 转换为 1）；

* 如果一个操作数是字符串，另一个操作数是数值，在比较相等性之前先将字符串转换为数值；

* 如果一个操作数是对象，另一个操作数不是，则调用对象的 valueOf\(\) 方法，用得到的基本类型值按照前面的规则进行比较；

* null 和 undefined 是相等的。 要比较相等性之前，不能将 null 和 undefined 转换成其他任何值。

* 如果有一个操作数是 NaN，则相等运算符返回 false，而不相等运算符返回 true。重要提示：即使两个操作数都是 NaN，相等运算符也返回 false；因为按照规则，NaN 不等于 NaN。

* 如果两个操作数都是对象，则比较它们是不是同一个对象。如果两个操作数都指向同一个对象，则相等运算符返回 true；否则，返回 false。


来看下面例子

```
console.log(null == undefined);  // true
console.log("NaN" == NaN);  // false
console.log(5 == NaN);  // false
console.log(NaN == NaN);  // false
console.log(NaN != NaN);  // true
console.log(false == 0);  // true
console.log(true == 1); // true
console.log(true == 2);  // false
console.log(undefined == 0);  // false
console.log(null == 0);  // false
console.log("5" == 5);  // true
```

**全等和不全等**

除了在比较之前不转换操作数之外，全等（`===`）和不全等（`!==`）运算符与相等和不相等运算符没有什么区别。它只在两个操作数值跟类型完成相等的情况下才返回 true，如下面的例子所示：

```
console.log("55" == 55);  // true，因为转换后相等
console.log("55" === 55);  // false，因为不同的数据类型不相等
console.log(null == undefined);  // true，因为它们是类似的值
console.log(null === undefined);  // false，因为它们是不同类型的值
```

### 条件运算符

条件运算符是一种三元运算符，其语法如下：

```
variable = boolean_expression ? true_value : false_value;
```

含义是：对 boolean\_express 求值，如果其结果为 true，则给变量 variable 赋 true\_value 值；如果其结果为 false，则给变量 variable 赋 false\_value 值。

来看下面例子：

```
var num1 = 10, 
    num2 = 20;
var max = (num1 > num2) ? num1 : num2;
console.log(max);  // 20
```

### 赋值运算符

简单的赋值运算符即等号（`=`），其作用是将右侧的值赋给左侧的变量，前面很多例子我们都已经用到过它了。这里就不再重复说明。

如果在等号（`=`）前面再添加乘性运算符、加性运算符等就可以为符合赋值操作符。

主要有以下几种：`*=`、`/=`、`%=`、`+=`、`-=`。

我们拿 `+=` 来说明符合赋值操作符的使用规则：

```
var num = 10;
num += 10; 
console.log(num);  // 20 

//相当于
var num = 10;
num = num + 10;
```

## 小结

以上介绍了常用的一些操作符，还有很多在本教程里面没有介绍。大家可以通过查询更多的资料来进行补充学习。

