# JavaScript 基础

JavaScript 是一种编程语言，它允许我们在网页上实现负责的东西。它是标准网络技术的第三层，在前面，我们已经学过前面两个：HTML 和 CSS 。

一起再回顾下：

HTML 是我们用于结构化和给 web 内容赋予意义的标记语言，如定义段落、标题、数据表格等等。

CSS 是一种样式规则语言，它能将我们定义的样式应用于 HTML 文档，如设置背景颜色、字体、元素大小等等。

而我们今天学的 JavaScript 则能够使我们的文档更具交互性，如动态更新内容、控制多媒体等等。

我们通过一个例子，HTML、CSS 和 JavaScript 到底是怎么协作的：

HTML：

```
<p>姓名：大宝</p>
```

![](/assets/js-base-html.jpg)

接着我们可以添加一些 CSS ，是它看上去好看些：

```
p {
    font-family: 'helvetica neue', helvetica, sans-serif;
    letter-spacing: 1px;
    text-transform: uppercase;
    text-align: center;
    border: 2px solid rgba(0,0,200,0.6);
    background: rgba(0,0,200,0.3);
    color: rgba(0,0,200,0.6);
    padding: 3px 10px;
    display: inline-block;
    cursor: pointer;
}
```

![](/assets/js-base-css.jpg)

到目前为止，显然上面这个按钮是没有任何交互行为的。接下来，我们就可以通过 JavaScript 给它添加一些动态行为：

```
var para = document.querySelector('p');

para.addEventListener('click', updateName);

function updateName() {
    var name = prompt('请输入一个新名字');
    para.textContent = '姓名：' + name;
}
```

此时，再点击按钮，发现会有一个弹窗出来，让我们输入名字，输入完成后，页面上会更新我们所输入的内容。

你可以点击 [这里](http://sandbox.runjs.cn/show/ef53v7vm) 查看效果。

此次，相信大家对 JavaScript 能做什么已经有个大致的印象了。当然，它能做的不仅如此。后续的课程，我们将一起探索。

（注：如果现在大家看不懂上面的代码，并没有关系，只要清楚 JavaScript 到底能做什么即可。）

