# 函数

函数是这样一段 JavaScript 代码，它只定义一次，但是可以被执行或调用任意次。

在 JavaScript 里，函数是对象，函数名实际上是一个指向函数对象的指针，不会与某个函数绑定。

## 函数定义

函数是用 function 关键字来定义的，有以下三种定义方式：

```
// 函数声明（推荐）
function sum (num1, num2) {
    return num1 + num2;
}

// 函数表达式（推荐）
var sum = function (num1, num2) {
    return num1 + num2;
};

// 用 Function 构造函数（不推荐）
var sum = new Function("num1", "num2", "return num1 + num2");
```

### 函数声明与函数表达式

函数声明跟函数表达式虽然在最终效果上是一样的，但是解析器在向执行环境中加载数据时，对它们并非一视同仁。

解析器会先读取函数声明，并使其在执行任何代码之前可用（可访问）；至于函数表达式，则必须等到解析器执行到它所在的代码行，才会真正被解释执行。看下面的例子：

```
console.log(sum(10, 10));  // 20
function sum (num1, num2) {
    return num1 + num2;
}
```

上面的代码可以正常执行，因为在代码开始执行之前，解析器就已经将函数声明提升到顶部，使其在整个执行环境中可使用。

我们再看下将上面的代码改完等价的函数表达式，是否会正常执行：

```
console.log(sum(10, 10));
var sum = function (num1, num2) {
    return num1 + num2;
}
```

直接报错了：sum is not a function ...

原因在于函数位于一个初始化语句中，而不是函数声明。在执行到函数所在的语句之前，变量 sum 中不会保存对函数的引用。所以导致了错误。

除了上面的区别，函数声明和函数表达式的语法其实等价的。

### 函数名

前面有提到过，函数名仅仅是指向函数的指针，所以一个函数可能会有多个名字，如下面的例子所示：

```
function sum (num1, num2) {
    return num1 + num2;
}
console.log(sum(10, 10));  // 20

var anotherSum = sum;
console.log(anotherSum(10, 10));  // 20

sum = null;
console.log(anotherSum(10, 10));  // 20
```

以上代码先定义了一个名为 sum 的函数，用于求两个值的和。然后，有声明了变量 anotherSum ，将其设置为与 sum 相等。此时，anotherSum 和 sum 都指向同一个函数，因此 anotherSum\(\) 可以被调用并返回结果。随即，又将 sum 设置为 null，只是销毁了它与函数的关系，但是 anotherSum 仍可以正常使用。

## 函数调用



