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

concat\(\) 方法不会改变原始数组。

### slice\(\)

slice\(\) 方法返回指定数组的一个片段或子数组。其语法如下：

```
arr.slice(begin) 
arr.slice(begin, end)
```

slice\(\)第一个参数为要抽取的片段的起始下标（包括begin），第二个参数为要抽取的片段的结尾下标（不包括end）。

看下面的例子：

```
var a = [1, 2, 3, 4, 5, 6];
var subArr = a.slice(0, 3);
console.log(subArr);  // [1, 2, 3]  下标分别为 0, 1, 2
```

可以只传递一个参数，返回从起始位置到数组结尾的所有元素：

```
var a = [1, 2, 3, 4, 5, 6];
var subArr = a.slice(3);
console.log(subArr);  // [4, 5, 6]
```

参数还可以为负数，则该参数规定的是从字符串的尾部开始算起的位置：

```
var a = [1, 2, 3, 4, 5, 6];
var subArr1 = a.slice(1, -1);
var subArr2 = a.slice(-3, -2);
var subArr3 = a.slice(-2, -3);
console.log(subArr1);  // [2, 3, 4, 5]
console.log(subArr2);  // [4]
console.log(subArr3);  // []
```

slice\(\) 方法不会改变原始数组。

### splice\(\)

splice\(\) 方法能在数组中插入或删除元素。其语法如下：

```
arr.splice(start)
arr.splice(start, deleteCount)
arr.splice(start, deleteCount, item1, item2, ...)
```

splice\(\) 的第一个参数指定了插入和（或）删除的起始位置。如果只指定一个参数，则从起始位置（包含start）开始到数组结尾的所有元素都将被删除：

```
var a = [1, 2, 3, 4, 5, 6];
var result = a.splice(4);
console.log(a);  // [1, 2, 3, 4]
console.log(result);  // [5, 6]
```

从上面的例子中，我们可以看出：splice\(\) 方法会修改原始数组，并且返回一个由删除元素组成的数组。

第一个参数还可以为负数，表示从数组结尾处规定位置：

```
var a = [1, 2, 3, 4, 5, 6];
var result = a.splice(-3);
console.log(a);  // [1, 2, 3]
console.log(result);  // [4, 5, 6]
```

splice\(\) 的第二个参数表示应该从数组中删除的元素个数，如果设置为 0，则不会删除元素：

```
var a = [1, 2, 3, 4, 5, 6];
console.log(a.splice(3, 0));  // []
console.log(a);  // [1, 2, 3, 4, 5, 6]
console.log(a.splice(2,3));  // [3, 4, 5]
console.log(a);  // [1, 2, 6]
```

从第三个参数开始，是指定了需要插入到数组中的元素，从第一个参数指定的位置开始插入：

```
var a = [1, 2, 3, 4, 5, 6];
console.log(a.splice(2, 0, "a", "b"));  // []
console.log(a);  // [1, 2, "a", "b", 3, 4, 5, 6]
console.log(a.splice(2, 2, [1, 2], "a"));  // ["a", "b"]
console.log(a);  // [1, 2, [1, 2], "a", 3, 4, 5, 6]
```

注意：splice\(\) 与 concat\(\) 不同，它会插入数组本身而不是数组元素。

### push\(\) 和 pop\(\)

push\(\) 和 pop\(\) 两个方法允许将数组当作栈来使用。

push\(\) 方法在数组尾部添加一个或多个元素，并返回新数组长度。其语法如下：

```
arr.push([element1[, ...[, elementN]]])
```

pop\(\) 方法则相反，它删除数组的最后一个元素，返回它删除的值。其语法如下：

```
arr.pop()
```

两个方法都是修改并替换原始数组。来看下面的例子：

```
var stack = [];
console.log(stack.push(1, 3, 5));  // 3
console.log(stack);  // [1, 3, 5]
console.log(stack.pop());  // 5
console.log(stack);  // [1, 3]
```

### unshift\(\) 和 shift\(\)

unshift\(\) 和 shift\(\) 两个方法行为类似 push\(\) 和 pop\(\)，不一样的是它们是在数组的头部而非尾部进行操作。

unshift\(\) 方法在数组头部添加一个或多个元素，返回新数组长度。其语法如下：

```
arr.unshift([element1[, ...[, elementN]]])
```

shift\(\) 方法删除数组第一个元素并将其返回。其语法如下：

```
arr.shift()
```

两个元素也都是修改并替换原始数组。看下面的例子：

```
var a = [];
console.log(a.unshift(5));  // 1
console.log(a.unshift(2));  // 2
console.log(a);  // [2, 5]
console.log(a.shift());  // 2
console.log(a);  // [5]
```

当使用多个参数调用 unshift\(\) 时，参数是一次性插入的，插入元素的顺序和它们在参数列表中的顺序一致：

```
var a = [];
console.log(a.unshift(2, 3, 4));  // 3
console.log(a);  // [2, 3, 4]
console.log(a.shift());  // 2
console.log(a.shift());  // 3
console.log(a);  // [4]
console.log(a.unshift(2));  // 2
console.log(a.unshift(3));  // 3
console.log(a);  // [3, 2, 4]
```

### forEach\(\)

forEach\(\) 方法从头至尾遍历数组，为每个元素调用指定回调函数。其语法如下：

```
arr.forEach(callback[, thisArg])
```

回调函数有三个参数，分别为：数组元素，元素索引和数组本身。

看下面的例子：

```
var a = [1, 2, 3, 4, 5];
var sum = 0;
a.forEach(function(v, i, a){
    a[i] = v + i;
}); 
console.log(a);  // [1, 3, 5, 7, 9]
```

注意：正常情况下，forEach\(\) 方法无法在所有元素都传递给回调函数前终止遍历。

### map\(\)

map\(\) 方法将调用数组的每个元素传递给指定的回调函数，并返回一个数组，它包含回调函数的返回值。其语法如下：

```
var new_array = arr.map(callback[, thisArg])
```

看下面的例子：

```
var a = [1, 2, 3];
var newArr = a.map(function(x){
    return x*x;
});
console.log(newArr);  // [1, 4, 9]
console.log(a);  // [1, 2, 3]
```

从上面的例子可以看出， map\(\) 函数返回的是新数组，不会修改原始数组。

### filter\(\)

filter\(\) 方法会创建一个新的数组，新数组的元素是通过检查指定数组中符合条件的所有元素。其语法如下：

```
var new_array = arr.filter(callback[, thisArg])
```

回调函数是用来逻辑判定的，返回 true 或 false。如果返回值为 true 或 能转化为 true 的值，那么传递给回调函数的元素就是新数组的子元素，如：

```
var a = [5, 4, 3, 2, 1];
var subArr = a.filter(function(x){
    return x < 3;
});
console.log(subArr);  // [2, 1]
console.log(a);  // [5, 4, 3, 2, 1]
```

从上面的例子同时可以看出，filter\(\) 方法同样不会改变原始数组。

### every\(\)

every\(\) 方法用于检测数组所有元素是否都符合指定条件（通过函数提供）。其语法如下：

```
arr.every(callback[, thisArg])
```

every\(\) 方法当且仅当针对数组中的所有元素调用判定函数都返回 true，它才返回 true。如果数组中检测到有一个元素不满足，则整个表达式返回 false ，且剩余的元素不会再进行检测。

看下面的例子：

```
var a = [1, 2, 3, 4, 5];
var result1 = a.every(function(x){
    return x < 10;
});
console.log(result1);  // true  
var result2 = a.every(function(x){
    return x % 2 === 0;
});
console.log(result2);  // false
```

### some\(\)

some\(\) 方法用来测试数组中的某些元素是否通过了指定函数的测试。其语法如下：

```
arr.some(callback[, thisArg])
```

some 为数组中的每一个元素执行一次回调函数，直到找到一个使得回调返回一个“真值”（即可转换为布尔值 true 的值）。如果找到了这样一个值，some 将会立即返回 true。否则，返回 false。

看下面的例子：

```
var a = [1, 2, 3, 4, 5];
var result1 = a.some(function(x){
    return x % 2 === 0;
});
console.log(result1);  // true
var result2 = a.some(isNaN);
console.log(result2);  // false
```

注意：map\(\)，filter\(\)，every\(\)，some\(\) 等方法的回调都包含三个参数：数组元素，元素索引和数组本身。

### reduce\(\) 和 reduceRight\(\)

reduce\(\) 和 reduceRight\(\) 方法使用指定函数将数组元素进行组合，生成单个值。

它们的语法分别如下：

```
arr.reduce(callback,[initialValue])
arr.reduceRight(callback[, initialValue])
```

其中，callback 回调函数可接受 4 个参数：

* previousValue —— 上一次调用回调的返回值，或提供的 initialValue

* currentValue —— 当前被处理的元素


* index —— 当前处理元素的索引

* array —— 调用 reduce 的数组


initialValue 可作为第一次调用回调 callback 的第一个参数。

来看下面的例子：

```
var a = [[0, 1], [2, 3], [4, 5]];
var result1 = a.reduce(function(a, b){ return a.concat(b)}, []);
console.log(result1);  // [0, 1, 2, 3, 4, 5]  
var result2 = a.reduceRight(function(a, b){ return a.concat(b)}, []);
console.log(result2);  // [4, 5, 2, 3, 0, 1]
```

从上面的例子可以看出两个方法的工作原理是一样的。但是，reduce\(\) 是按照数组索引从底到高（即从左到右）处理数据。而 reduceRight\(\) 则是按照数组索引从高到低（即从右到左）处理数据。

### indexOf\(\) 和 lastIndexOf\(\)

indexOf\(\) 和 lastIndexOf\(\) 搜索整个数组中具有给定值的元素，返回找到的第一个元素的索引，如果没有找到则返回 -1。

它们的语法如下：

```
arr.indexOf(searchElement[, fromIndex = 0])
rr.lastIndexOf(searchElement[, fromIndex = arr.length - 1])
```

indexOf\(\) 是从头至尾搜索，而lastIndexOf\(\) 则反向搜索。

看下面的例子：

```
var a = [0, 1, 2, 1, 0];
console.log(a.indexOf(1));  // 1
console.log(a.lastIndexOf(1));  // 3
```

这两个方法还有一个可选参数，指定数组中的一个索引，表示从该索引处开始搜索。这个参数也可以是负数，表示相对数组末尾的偏移量，-1 表示数组最后一个元素。

看下面的例子：

```
var a = [0, 1, 2, 1, 0];
console.log(a.indexOf(1, 3));  // 3
console.log(a.indexOf(1, -2));  // 3
```

## 数组类型

在 ES5 中，可以用 Array.isArray\(\) 函数检测是否为数组：

```
console.log(Array.isArray([]));  // true
console.log(Array.isArray({}));  // false 
```

ES5 前可以用以下函数代替 isArray\(\)：

```
var isArray = Function.isArray || function(o) {
    return typeof o === "object" && 
    Object.prototype.toString.call(o) === "[object Array]";
}
```

## 小结

在这个小节中，我们介绍了数组的创建、数组元素的读写、稀疏数组、数组长度、数组方法以及判断数组的方法。这里介绍的都是比较常用的数组相关知识，如想要了解更多更详细的内容，可以查看[数组对象API](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)。

