# 数组

数组是值的有序集合。每个值叫做一个元素，每个元素在数组中有一个对应的位置，称为索引，索引从 0 开始。

在 JavaScript 中，数组是无类型的，即数组元素可以是任意类型。并且它是动态的，会根据需要增长或缩减。

## 创建数组

我们可以使用数组直接量来创建数组，在方括号中将数组元素用逗号隔开，如下：

```
var arr1 = [];  // 创建一个空数组
var arr2 = [2, 3, 4];  // 创建一个有3个值得数组
var arr3 = [true, 1.2, "str", [1, 3], {x: 1, y: 2}];  // 创建一个元素为不同类型的数组
```

我们还可以使用数组的构造函数 Array\(\) 来创建数组。这里有三种不同的情况：

**调用时没有参数：**

```
var arr1 = new Array();
```

上面的代码表示创建一个没有任何元素的空数组，相当于：

```
var arr1 = [];
```

**调用时有一个数值参数：**

```
var arr2 = new Array(3);
```

上面的代码表示创建一个长度为 3 的数组，这三个元素值未被定义，相当于：

```
var arr2 = [,,,];
```

**显示指定两个或多个数组元素或一个非数值元素：**

```
var arr3 = new Array(2, 4);
var arr4 = new Array("a");
```

此时，都是将参数作为数组的元素，上面的例子相当于：

```
var arr3 = [2, 4];
var arr4 = ["a"];
```

通过上面的例子，可以看出，使用数组字面量来创建数组会比使用 Array\(\) 构造函数要简单的多。所以我们也推荐使用字面量来创建数组。

## 数组元素的读写

可以使用 `[] 来访问数组的元素，[] 内为非负整数值：`

```
var a = ["hello", "world"];
// 索引从 0 开始
console.log(a[0]);  // "hello"
console.log(a[1]);  // "world"
```

如果需要修改数组元素的值，可以这样处理：

```
var a = ["hello", "world"];
console.log(a[1]);  // "world"
a[1] = "cat";  // 改写数组第二个元素
console.log(a[1]);  // "cat"
```

## 数组长度

每个数组都有一个 `length 属性，用于标识数组的长度，即数组元素的个数。来看下面的例子：`

```
console.log([].length);  // 0，该数组没有元素
var arr = ["a", "b", "c"];  
console.log(arr.length);  // 3
```

### 稀疏数组

通常情况下，数组长度都是等于其元素的个数。但是有一种数组除外，即稀疏数组。

稀疏数组就是包含从 0 开始的不连续索引的数组，其 `length 属性值大于元素个数。`

看下面的例子：

```
var arr1 = new Array(5);
console.log(arr1.length);  // 5。数组没有元素，但是其长度为5
var arr2 = [];
console.log(arr2.length);  // 0
arr2[1000] = 0;
console.log(arr2.length);  // 1001 ，长度为1001，只有第1001个元素有值
```

注意，以上例子省略的元素在数组中其实是存在的，值为 `undefined 。`

同时，我们还能得出一个结论：如果为一个数组元素赋值，它的索引 `i 大于或等于现有数组长度时，length 属性的值将自动设置为 i+1。`

另外，数组的 length 属性还有一个特殊行为，即当设置 length 属性为一个小于当前长度的非负整数 n 时，当前数组中那些索引大于或等于 n 的元素将从数组中删除：

```
var arr = [1, 2, 3, 4, 5]; 
console.log(arr.length);  // 5
arr.length = 3;
console.log(arr);  // [1, 2, 3]
arr.length = 0;
console.log(arr);  // []
arr.length = 5;  // 相当于 new Array(5)
console.log(arr[4]);  // undefined
```

## 数组遍历

使用 for 循环来遍历数组是最常见的方法：

```
var arr = ["a", "b", "c", "d"];
for (var i = 0; i < arr.length; i++) {
    console.log(i + ': ' + arr[i]);
}
```

上面的代码将在控制台中输出以下结果：

![](/assets/js-arr-for.jpg)

但是在这个例子中，还有需要优化的地方：数组长度没有必要每次都去查询，只需要查询一次即可。 for 循环条件不符可以改写为：

```
for (var i = 0, len = arr.length; i < len; i++) {
    // 循环体不变
}
```

有些时候我们可能并不清楚数组元素是否均存在。此时，我们在使用前可能需要先检测它们。

如果想排除 null、undefined 和不存在的元素，可以像这样判断：

```
for (var i = 0, len = arr.length; i < len; i++) {
    if (!a[i]) continue;  // 跳过 null、undefined 和不存在的元素
    // 循环体
}
```

如果只想跳过 undefined 和不存在的元素，可以像这样判断：

```
for (var i = 0, len = arr.length; i < len; i++) {
    if (a[i] === undefined) continue;  // 跳过 undefined 和不存在的元素
    // 循环体
}
```

最后，如果只想跳过不存在的元素而仍然要处理存在的 undefined 元素，判断代码如下：

```
for (var i = 0, len = arr.length; i < len; i++) {
    if (!(i in a)) continue;  // 跳过不存在的元素
    // 循环体
}
```

还可以使用 for/in 循环处理稀疏数组。循环每次将一个可枚举的属性名（包括数组索引）赋值给循环变量，不存在的索引将不会遍历到。例如：

```
for(var index in sparseArray) {
   var value = sparseArray[index];
   // 此处可以使用索引和值做一些事情
}
```

但由于 for/in 循环能够枚举继承的属性名，如添加到 `Array.prototype 中的方法。基于这个原因，在数组上不应该使用 for/in 循环，除非使用额外的检测方法来过滤不想要的属性。例如：`

```
for(var i in a) {
    // 跳过继承的属性
    if (!a.hasOwnProperty(i)) continue;

    // 跳过不是非负整数的 i
    if (String(Math.floor(Math.abs(Number(i)))) !== i) continue;
}
```

ES 5 定义了一些遍历数组元素的新方法，按照索引的顺序按个传递给定义的一个函数。这些方法中最常用的就是 `forEach() 方法。例如：`

```
var data = [1,2,3,4,5];     // 这是需要遍历的数组
var sumOfSquares = 0;       // 要得到数据的平方和
data.forEach(function (x) {  // 把每个元素传递给此函数
    sumOfSquares += x*x;    // 平方相加
});
console.log(sumOfSquares);  // 55. (1 + 4 + 9 + 16 + 25)
```

## 数组方法

在 Array.prototype 中定义了一些很有用的操作数组的方法，接下来我们将一些来学习这些方法。

### join\(\)

join\(\) 方法将数组中所有元素都转化为字符串并连接在一起，最后返回生成的字符串。其语法如下：

```
arr.join()  // 未显示指定分隔符
arr.join(separator)  // 显示指定分隔
```

arr 为需要转化的数组，separator 为需要分隔符。

如果不指定分隔符，默认使用逗号，否则使用指定的分隔符。如下面代码所示：

```
var arr = [1, 3, 5];  // 创建一个数组
console.log(arr.join());  // 1,3,5
console.log(arr.join("-"));  // 1-3-5
```

### reverse\(\)

reverse\(\) 方法将数组元素颠倒排序，返回逆序数组。其语法如下：

```
arr.reverse()
```

这个方法是直接操作在原数组上的，不会创建新数组：

```
var arr = [1, 3, 5]; 
arr.reverse();
console.log(arr);  // [5, 3, 1]
```

### sort\(\)

sort\(\) 方法将数组中的元素排序并返回排序后的数组。其语法如下：

```
arr.sort()  // 不带参数
arr.sort(compareFunction)  // 待参数
```

不带参数时调用 sort\(\) 方法，数组元素将按照字母表顺序排序：

```
var arr = ["banana", "cherry", "apple"];
arr.sort();
console.log(arr);   //["apple", "banana", "cherry"]
```

需要注意的是，如果数组内含有 undefined 元素，它们将会被排到数组末尾。

我们还可以给 sort\(\) 方法传递一个比较函数。该函数决定了它的两个参数在排好序的数组中的先后顺序。假设第一个参数应该在前，比较函数应该返回一个小于 0 的数值。反之，假设第一个参数应该在后，函数应该返回一个大于 0 的数值。并且，假设两个值相等，函数返回 0 。看下面的例子：

```
var arr = [33, 4, 120, 220];
arr.sort();  // [120, 220, 33, 4]
console.log(arr); 
arr.sort(function(a, b){
    return a-b;
});
console.log(arr);  // [4, 33, 120, 220]
```

### concat\(\)

concat\(\) 方法用于连接数组。它会创建并返回一个新数组，新数组元素包含原始数据元素和 concat\(\) 的每个参数。其语法如下：

```
var new_array = old_array.concat(value1[, value2[, ...[, valueN]]])
```

看下面的例子：

```
var arr = [1, 3, 5];
var newArr = arr.concat(7, 9);
console.log(newArr);  // [1, 3, 5, 7, 9]
```

如果参数自身是一个数组，则链接的是数组的元素，如：

```
var arr = [1, 3, 5];
var newArr = arr.concat([7, 9], 2);
console.log(newArr);  // [1, 3, 5, 7, 9, 2]
```

另外，concat\(\) 不会递归扁平化数组的元素，如：

```
var arr = [1, 3, 5];
var newArr = arr.concat([2, [4, 6]]);
console.log(newArr);  // [1, 3, 5, 2, [4, 6]];
```



