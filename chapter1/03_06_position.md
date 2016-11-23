#CSS 定位
## 概念

###### CSS 定位 (Positioning) 属性允许你对元素进行定位。

CSS定位属性允许你为一个元素定位。它也可以将一个元素放在另一个元素后面，并指定一个元素的内容太大时，应该发生什么。元素可以使用的顶部，底部，左侧和右侧属性定位。然而，这些属性无法工作，除非是先设定position属性。


###### CSS 定位和浮动

CSS 为定位和浮动提供了一些属性，利用这些属性，可以建立列式布局，将布局的一部分与另一部分重叠，还可以完成多年来通常需要使用多个表格才能完成的任务。

定位的基本思想很简单，它允许你定义元素框相对于其正常位置应该出现的位置，或者相对于父元素、另一个元素甚至浏览器窗口本身的位置。显然，这个功能非常强大，也很让人吃惊。要知道，用户代理对 CSS2 中定位的支持远胜于对其它方面的支持，对此不应感到奇怪。

###### 一切皆为框

`div`、`h1 `或 `p `元素常常被称为块级元素。这意味着这些元素显示为一块内容，即“块框”。与之相反，`span` 和` strong` 等元素称为“行内元素”，这是因为它们的内容显示在行中，即“行内框”。

可以使用 `display `属性改变生成的框的类型。这意味着，通过将 `display` 属性设置为 `block`，可以让行内元素（比如 `a` 元素）表现得像块级元素一样。还可以通过把 `display` 设置为 `none`，让生成的元素根本没有框。这样的话，该框及其所有内容就不再显示，不占用文档中的空间。

但是在一种情况下，即使没有进行显式定义，也会创建块级元素。这种情况发生在把一些文本添加到一个块级元素（比如 `div`）的开头。即使没有把这些文本定义为段落，它也会被当作段落对待：

    <div>
    some text
    <p>Some more text.</p>
    </div>


###### CSS 定位机制

CSS 有三种基本的定位机制：普通流、浮动和绝对定位。

==除非专门指定，否则所有框都在普通流中定位==。也就是说，普通流中的元素的位置由元素在 (X)HTML 中的位置决定。

块级框从上到下一个接一个地排列，框之间的垂直距离是由框的垂直外边距计算出来。

行内框在一行中水平布置。可以使用水平内边距、边框和外边距调整它们的间距。但是，垂直内边距、边框和外边距不影响行内框的高度。由一行形成的水平框称为行框（Line Box），行框的高度总是足以容纳它包含的所有行内框。不过，设置行高可以增加这个框的高度。

在下面的章节，我们会为您详细讲解相对定位、绝对定位和浮动。

###### CSS position 属性

通过使用 position 属性，我们可以选择 4 种不同类型的定位，这会影响元素框生成的方式。

position 属性值的含义：

- static
    元素框正常生成。块级元素生成一个矩形框，作为文档流的一部分，行内元素则会创建一个或多个行框，置于其父元素中。==如果未显式声明元素的定位类型，则默认为该值。==
- relative
    元素框偏移某个距离。元素仍保持其未定位前的形状，它原本所占的空间仍保留。
- absolute
    元素框从文档流完全删除，并相对于其包含块定位。包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。
- fixed
    元素框的表现类似于将 position 设置为 absolute，不过其包含块是视窗本身。


==提示：== 相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。



###### CSS 定位属性


 属性| 描述
---|---
position  |	 把元素放置到一个静态的、相对的、绝对的、或固定的位置中。
top  |	定义了一个定位元素的上外边距边界与其包含块上边界之间的偏移。
right  |	定义了定位元素右外边距边界与其包含块右边界之间的偏移。
bottom |	定义了定位元素下外边距边界与其包含块下边界之间的偏移。
left |	定义了定位元素左外边距边界与其包含块左边界之间的偏移。
overflow |	设置当元素的内容溢出其区域时发生的事情。
clip |	设置元素的形状。元素被剪入这个形状之中，然后显示出来。
vertical-align |	设置元素的垂直对齐方式。
z-index |	设置元素的堆叠顺序。



## 相对定位

设置为相对定位的元素框会偏移某个距离。元素仍然保持其未定位前的形状，它原本所占的空间仍保留。

###### CSS 相对定位

相对定位是一个非常容易掌握的概念。如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直或水平位置，让这个元素“相对于”它的起点进行移动。

如果将 top 设置为 20px，那么框将在原位置顶部下面 20 像素的地方。如果 left 设置为 30 像素，那么会在元素左边创建 30 像素的空间，也就是将元素向右移动。

    #box_relative {
      position: relative;
      left: 30px;
      top: 20px;
    }

如下图所示：

![](http://www.w3school.com.cn/i/ct_css_positioning_relative_example.gif)

注意，在使用相对定位时，无论是否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。

## 绝对定位

设置为绝对定位的元素框从文档流完全删除，并相对于其包含块定位，包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像该元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。

###### CSS 绝对定位

绝对定位使元素的位置与文档流无关，因此不占据空间。这一点与相对定位不同，相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。

普通流中其它元素的布局就像绝对定位的元素不存在一样：

    #box_relative {
      position: absolute;
      left: 30px;
      top: 20px;
    }

如下图所示：

![](http://www.w3school.com.cn/i/ct_css_positioning_absolute_example.gif)

绝对定位的元素的位置相对于==最近的已定位祖先元素==，如果元素没有已定位的祖先元素，那么它的位置相对于最初的包含块。

对于定位的主要问题是要记住每种定位的意义。所以，现在让我们复习一下学过的知识吧：相对定位是“相对于”元素在文档中的初始位置，而绝对定位是“相对于”最近的已定位祖先元素，如果不存在已定位的祖先元素，那么“相对于”最初的包含块。

注释：根据用户代理的不同，最初的包含块可能是画布或 HTML 元素。

因为绝对定位的框与文档流无关，所以它们可以覆盖页面上的其它元素。可以通过设置 `z-index` 属性来控制这些框的堆放次序。


## 固定定位

固定定位 `fixed `和绝对定位 `position` 相似，都是脱离文档流，不过绝对定位是相对与父元素的定位，固定定位总是以`body`为定位时的对象，总是根据浏览器的窗口来进行元素的定位，通过"left"、 "top"、 "right"、 "bottom" 属性进行定位。

我们了解了fixed属性的说明后，就可以知道它的作用了。当我们需要使一个层相对于浏览器来自动调整该层的位置的时候，如果你使用position的absolute属性来定位该层，你会发现absolute属性并不能达到你想要的css效果，。这时，就需要要用到fixed属性来定位该层了。

如下

     p.one
            {
                position:fixed;
                left:5px;
                top:5px;
                }
     p.two
            {
                position:fixed;
                top:30px;
                right:5px;
                }

## 层级

z-index 属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。

如下例子

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>css定位--层级</title>
        <link rel="stylesheet" href="css/style.css">
        <style>
            div{
                position:relative;
                }
            p{
                position:absolute;
                width:200px;
                height:200px;
                border:1px solid #ff0000;
                }
            .pos-1{
                z-index:2;
                background:yellow;
                }
            .pos-2{
                z-index:1;
                left:100px;
                top:100px;
                background:#ff0000;
                }
        </style>
    </head>
    <body>
        <div>
            <p class="pos-1">第一个元素z-index为2;</p>
            <p class="pos-2">第二个元素z-index为1;</p>
        </div>
    </body>
    </html>

注意

- 元素可拥有负的 z-index 属性值。(该属性设置一个定位元素沿 z 轴的位置，z 轴定义为垂直延伸到显示区的轴。如果为正数，则离用户更近，为负数则表示离用户更远。)
- z-index 仅能在定位元素上奏效（例如 position:absolute;）！

如下例子

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>css定位--层级</title>
        <link rel="stylesheet" href="css/style.css">
        <style>
            div{
                border:1px dashed red;
                position:relative;
                }
            img.x
            {
                position:absolute;
                left:0px;
                top:0px;
                z-index:-1
                }
        </style>
    </head>
    <body>
        <div>
            <h1>这是一个标题</h1>
            <img class="x" src="images/bg.gif" />
            <p>默认的 z-index 是 0。图片的z-index -1 拥有更低的优先级。所以图片会被文字挡住</p>
        </div>
    </body>
    </html>


可能的值


值 | 描述
---|---
auto | 默认。堆叠顺序与父元素相等。
number 	|  设置元素的堆叠顺序。
inherit | 规定应该从父元素继承 z-index 属性的值。




###### 层级关系

- 首先是遵循DOM的规则，同级的后面居上。

- 一般有定位属性的元素会高于无定位属性的同级元素。

- 都有定位属性的同级元素，z-index大者居上

- 如果是非同级的元素， 则会忽略元素本身z-index，取与对比元素同级的祖先元素的z-index属性，大者居上 。 

## 浮动


浮动的框可以向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。

由于浮动框不在文档的普通流中，所以文档的普通流中的块框表现得就像浮动框不存在一样。


###### CSS 浮动

请看下图，当把框 1 向右浮动时，它脱离文档流并且向右移动，直到它的右边缘碰到包含框的右边缘：

![](http://www.w3school.com.cn/i/ct_css_positioning_floating_right_example.gif)

再请看下图，当框 1 向左浮动时，它脱离文档流并且向左移动，直到它的左边缘碰到包含框的左边缘。因为它不再处于文档流中，所以它不占据空间，实际上覆盖住了框 2，使框 2 从视图中消失。

再请看下图，当框 1 向左浮动时，它脱离文档流并且向左移动，直到它的左边缘碰到包含框的左边缘。因为它不再处于文档流中，所以它不占据空间，实际上覆盖住了框 2，使框 2 从视图中消失。

![](http://www.w3school.com.cn/i/ct_css_positioning_floating_left_example.gif)

如下图所示，如果包含框太窄，无法容纳水平排列的三个浮动元素，那么其它浮动块向下移动，直到有足够的空间。如果浮动元素的高度不同，那么当它们向下移动时可能被其它浮动元素“卡住”：

![](http://www.w3school.com.cn/i/ct_css_positioning_floating_left_example_2.gif)

###### css float 属性

float 属性定义元素在哪个方向浮动。以往这个属性总应用于图像，使文本围绕在图像周围，不过在 CSS 中，任何元素都可以浮动。浮动元素会生成一个块级框，而不论它本身是何种元素。

如果浮动非替换元素，则要指定一个明确的宽度；否则，它们会尽可能地窄。

假如在一行之上只有极少的空间可供浮动元素，那么这个元素会跳至下一行，这个过程会持续到某一行拥有足够的空间为止。

可能的值


值 	 | 描述
---|---
left  |	元素向左浮动。
right |	元素向右浮动。
none  |	默认值。元素不浮动，并会显示在其在文本中出现的位置。
inherit  |	规定应该从父元素继承 float 属性的值。

###### 行框和清理

浮动框旁边的行框被缩短，从而给浮动框留出空间，行框围绕浮动框。

因此，创建浮动框可以使文本围绕图像：

![](http://www.w3school.com.cn/i/ct_css_positioning_floating_linebox.gif)

要想阻止行框围绕浮动框，需要对该框应用 clear 属性。clear 属性的值可以是 left、right、both 或 none，它表示框的哪些边不应该挨着浮动框。

为了实现这种效果，在被清理的元素的上外边距上添加足够的空间，使元素的顶边缘垂直下降到浮动框下面：

![](http://www.w3school.com.cn/i/ct_css_positioning_floating_clear.gif)

这是一个有用的工具，它让周围的元素为浮动元素留出空间。

让我们更详细地看看浮动和清理。假设希望让一个图片浮动到文本块的左边，并且希望这幅图片和文本包含在另一个具有背景颜色和边框的元素中。可能编写下面的代码：

    .news {
      background-color: gray;
      border: solid 1px black;
      }
    
    .news img {
      float: left;
      }
    
    .news p {
      float: right;
      }
    
    <div class="news">
    <img src="news-pic.jpg" />
    <p>some text</p>
    </div>
这种情况下，出现了一个问题。因为浮动元素脱离了文档流，所以包围图片和文本的 div 不占据空间。

如何让包围元素在视觉上包围浮动元素呢？需要在这个元素中的某个地方应用 clear：

![](http://www.w3school.com.cn/i/ct_css_positioning_floating_clear_div.gif)

不幸的是出现了一个新的问题，由于没有现有的元素可以应用清理，所以我们只能添加一个空元素并且清理它。

    .news {
      background-color: gray;
      border: solid 1px black;
      }
    
    .news img {
      float: left;
      }
    
    .news p {
      float: right;
      }
    
    .clear {
      clear: both;
      }
    
    <div class="news">
    <img src="news-pic.jpg" />
    <p>some text</p>
    <div class="clear"></div>
    </div>

这样可以实现我们希望的效果，但是需要添加多余的代码。常常有元素可以应用 clear，但是有时候不得不为了进行布局而添加无意义的标记。

不过我们还有另一种办法，那就是对容器 div 进行浮动：

    .news {
      background-color: gray;
      border: solid 1px black;
     
      }
    .news-f{
            float:left;

            }
    .news img {
      float: left;
      }
    
    .news p {
      float: right;
      }
    
    <div class="news news-f">
    <img src="news-pic.jpg" />
    <p>some text</p>
    </div>

这样会得到我们希望的效果。不幸的是，下一个元素会受到这个浮动元素的影响。为了解决这个问题，有些人选择对布局中的所有东西进行浮动，然后使用适当的有意义的元素（常常是站点的页脚）对这些浮动进行清理。这有助于减少或消除不必要的标记。

最后，还有一种方法，就是使用伪类，应用clear清楚浮动，但是要注意，必须把这个伪类为块级元素，清楚高度，行高，还有可见性。在IE7，因为IE7不支持:after伪类，这个神奇的zoom:1让IE6的元素可以清除浮动来包裹内部元素

例子如下

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>css定位-浮动</title>
        <link rel="stylesheet" href="css/style.css">
        <style>
             .news {
                 background-color: gray;
                 border: solid 1px black;
                 }
         
             .news img {
                 float: left;
                 }
    
             .news p {
                 float: right;
                 }
             
             .clearfix:after{
                 content: "";
                 display: block;/*加入的这个元素转换为块级元素。*/
                 height: 0;
                 clear: both;/*清除左右两边浮动。*/
                 }
             .clearfix{
                 zoom:1;/*这是针对于IE7的，因为IE7不支持:after伪类，这个神奇的zoom:1让IE6的元素可以清除浮动来包裹内部元素。*/
                 }
    
        </style>
    </head>
    <body>
    
        <div class="news clearfix">
            <img src="images/bg.gif">
            <p>This is some text. This is some text. This is some text. This is some text. </p>
        </div>
    
    </body>
    </html>


###### CSS clear 属性

clear 属性定义了元素的哪边上不允许出现浮动元素。在 CSS1 和 CSS2 中，这是通过自动为清除元素（即设置了 clear 属性的元素）增加上外边距实现的。在 CSS2.1 中，会在元素上外边距之上增加清除空间，而外边距本身并不改变。不论哪一种改变，最终结果都一样，如果声明为左边或右边清除，会使元素的上外边框边界刚好在该边上浮动元素的下外边距边界之下。


值 |描述
---|---
left   |	在左侧不允许浮动元素。
right  |	在右侧不允许浮动元素。
both  |	在左右两侧均不允许浮动元素。
none  |	默认值。允许浮动元素出现在两侧。
inherit  |	规定应该从父元素继承 clear 属性的值。



