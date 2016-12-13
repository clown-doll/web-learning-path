# 函数

函数是这样一段 JavaScript 代码，它只定义一次，但是可以被执行或调用任意次。

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
}

// 用 Function 构造函数（不推荐）
var sum = new Function("num1", "num2", "return num1 + num2");
```



