## CSS
### 1. 概述
CSS指层叠样式表，CSS样式表极大地提高了工作效率
### 2. 基本语法
```
selector{
    property:value
}
```
### 2.1 属性大于一个，需要用分号隔开
```
h1{
    color:red;
    font-size:14px;
}
```   
### 2.2 值大于一个单词，需要加上引号
```
p{
  font-family:"sans serif";
}
```
### 3. 高级语法
#### 3.1 选择器分组
```
h1,h2,h3,h4,h5,h6{ 
    color:red;
}   
``` 
#### 3.2 继承
```
body{
    color:green;
}
```
### 4. 派生选择器
通过依据元素在其位置的上下文关系来定义样式 <br>
```
<!--html-->
<p><strong>P标签里的strong</strong></p>
<ul>
<li><strong>li标签里的strong</strong></li>
</ul>
/*css*/
li strong{
    color: blue;
}
```
### 5. `id`选择器
#### 5.1 定义
- `id`选择器可以为标有`id`的HTML元素指定特定的样式
- `id`选择器以"`#`"来定义
```
<!--html-->
<div id="divID">这是一个divID</div>
/*css*/
#divID{
   color: darkblue;
}
```
#### 5.2 `id`选择器和派生选择器
目前比较常用的方式是`id`选择器常常用于建立派生选择器 <br>
```
<!--html-->
<p id="pID">这是一个pID<a href="http://www.google.co.jp">谷歌</a></p>
/*css*/
#pID a{
   color: #ff0059;
}
```
### 6. `class`选择器
- `class`选择器以`"."`来定义 <br>
```
<!--html-->
<div class="divClass">divClass</p>
/*css*/
.divClass{
    color: cornflowerblue;
}
```
- `class`选择器可以用作派生选择器 <br>
```
<!--html-->
<p class="pClass">这是一个class<a href="http://www.google.co.jp">谷歌</a></p>
/*css*/
.pClass a{
    color: forestgreen;
}
```
- `class` 在一个元素上可以同时应用多个class，通过空格来分割 <br/>
如: `<img class="class1 class2">`
```
 <a href="#"><img class="smaller-image thick-green-border" src="cat.jpg" alt="萌猫"></a>
```
### 7. 属性选择器
#### 7.1 属性选择器
对带有指定属性的HTML元素设置样式
#### 7.2 属性和值选择器
```
<style type="text/css">
    [title]{
        color: chocolate;
    }
    [title=te]{
        color: darkcyan;
    }
</style>  
<p title="t">属性选择器</p>
<p title="te">属性和值选择器</p>
```
### 8. 样式
#### 8.1 背景
##### 8.1.1 定义
CCS允许应用纯色作为背景，也允许使用背景图像创建相当复杂的效果
##### 8.1.2 属性
- `background-color`: 设置元素的背景颜色 <br>
```
p{
  width: 130px;
  padding: 10px;
  background-color: forestgreen;
}
```   
- `background-image`: 把图片设置为背景 <br>
```
body{
    background-image:url("../../pic/yaoyao.jpeg") ;
}
```
- `background-position`: 设置背景图片的起始位置 <br>
```
body{
    background-image: url("../../pic/cat.jpg");
    background-repeat: no-repeat;
    background-position: right top;
}
```
- `background-repeat`: 设置背景图片是否及如何重复 <br>
```
body{
    background-image: url("../../pic/yaoyao.jpeg");
    background-repeat: no-repeat;
}
```
- `background-attachment`: 背景图像是否固定或者随页面的其余部分滚动 <br>
```
body{
    background-image: url("../../pic/cat.jpg");
    background-repeat: no-repeat;
    background-attachment: fixed;
}
```
- `background-size`: 规定背景图片的尺寸 <br>
  `background-size: 200px 200px`;
- `background-origin`: 规定背景图片的定位区域
- `background-clip`: 规定背景的绘制区域
#### 8.2 文本
CSS文本属性可定义文本外观 <br>
通过文本属性，可以改变文本的颜色，字符间距，对齐文本，装饰文本，对文本缩进 <br>
- `color`: 文本颜色
- `direction`: 文本方向
- `line-height`: 行高
- `letter-spacing`: 字符间距
- `text-align`: 对齐元素中的文本
- `text-decoration`: 向文本添加修饰
- `text-indent`: 缩进元素中文本的首行 <br>
   `text-indent:2em;`
- `text-transform`: 元素中的字母
```
/*字母全部小写：*/
text-transform: lowercase;
/*字母全部大写：*/
text-transform: uppercase;
/*首字母大写：*/
text-transform: capitalize;
```
- `unicode-bidi`: 设置文本方向 
- `white-space`: 元素中空白的处理方式
- `word-spacing`: 字间距
- `text-shadow`: 向文本添加阴影 <br>
  `text-shadow: 0px 0px 5px red;`
- `word-wrap`：规定文本的换行规则
```
width:100px;
text-wrap:normal;
```
#### 8.3 字体
CSS字体属性定义文本的字体系列，大小，加粗，风格和变形
- `font-family`: 设置字体系列
所有浏览器都有几种默认字体。这些通用字体包括`monospace`，`serif`和`sans-serif`。
当字体不可用，你可以告诉浏览器通过 “降级” 去使用其他字体。
例如，如果你想将一个元素的字体设置成`Helvetica`，当`Helvetica`不可用时，降级使用`sans-serif`字体，那么可以这样写：
```
p {
  font-family: Helvetica, sans-serif;
}
```
- `font-size`: 设置字体的尺寸
- `font-style`: 设置字体的风格
- `font-variant`: 以小型大写字体或正常字体显示文本
- `font-weight`: 设置字体的粗细
#### 8.4 链接
##### 8.4.1 四种状态
- `a:link`: 普通的，未被访问的链接
- `a:visited`: 用户已访问的链接
- `a:hover`: 鼠标指针位于链接的上方
- `a:active`: 链接被点击的时刻
##### 8.4.2 常见的链接样式
- `text-decoration`: 大多用于去掉链接中的下划线 
##### 8.4.3 设置背景颜色
- `background-color`
##### 8.4.4 例子
```
a:link{
       color: red;
       text-decoration: none;
       background-color: cornflowerblue;
}
```
#### 8.5 列表
允许放置，改变列表标志，或者将图像作为列表项标志 <br>
- `list-style`: 简写列表项
- `list-style-image`: 列表项图像
```
ul li{
     list-style-image: url("../../pic/cat.jpg");
}
```
- `list-style-position`: 列表标志位置
```
ul.ul1{
     list-style-position: inside;
}
ul.ul2{
     list-style-position: outside;
}
```
- `list-style-type`: 列表类型
```
ul li{
    list-style-type: circle;
}
/*去掉list前面的标志符号*/
list-style-type:none;
```
#### 8.6 表格
##### 8.6.1 CSS表格属性可以极大改善表格的外观
##### 8.6.2 属性
- `border`: 表格边框
```
#tb,tr,th,td{
    border: 2px solid blueviolet;
}
```
- `border-collapse`: 折叠边框
```
#tb{
    border-collapse: collapse;
}
```  
- `width`，`height`：表格宽高
```
#tb{
    width: 200px;
    height: 200px;
}
```   
- `text-align`：表格文本对齐
- `padding`：表格内边距
- `background-color`：表格颜色
#### 8.7 轮廓
##### 8.7.1 定义
用来突出元素的作用
##### 8.7.2 属性
- `outline`: 设置轮廓属性
- `outline-color`: 设置轮廓颜色
- `outline-style`: 设置轮廓样式
- `outline-width`: 设置轮廓宽度
##### 8.7.3 例子
```
p{
  outline-width:2px;
  outline-color:blue;
  outline-style:dotted; 
}
```
### 9. 定位
#### 9.1 定位
##### 9.1.1 CSS定位
改变元素在页面上的位置
##### 9.1.2 CSS定位机制
- 普通流：元素按照其在HTML中的位置顺序决定排布的过程
- 浮动
- 绝对布局
##### 9.1.3 CSS定位属性
- `position`: 把元素放在一个静态的，相对的，绝对的或固定的位置中 <br>
   - static: 对偏移量不起任何效果
   - relative
   - absolute
   - fixed
- `top`: 元素向上的偏移量
- `left`: 元素向左的偏移量
- `right`: 元素向右的偏移量
- `bottom`: 元素向下的偏移量
- `overflow`: 设置元素溢出其区域发生的事情
- `clip`：设置元素显示的形状
- `vertical-align`: 设置元素垂直对齐方式
- `z-index`: 设置元素的堆叠顺序，值越大越呈现在前面
```
#position1{
    width: 100px;
    height: 100px;
    background-color: cornflowerblue;
    position: relative;
    left: 20px;
    top:20px;
    z-index: 2;
}
#position2{
    width: 100px;
    height: 100px;
    background-color: red;
    position: relative;
    left: 10px;
    top:10px;
    z-index: 1;
}
```
#### 9.2 浮动
##### 9.2.1 float属性
- `left`: 元素向左浮动
- `right`: 元素向右浮动
- `none`: 元素不浮动
- `inherit`: 从父级继承浮动属性
##### 9.2.2 clear属性：去掉浮动属性（包括继承来的属性）
- `left`: 去掉元素向左浮动
- `right`: 去掉元素向右浮动
- `both`: 左右两侧均去掉浮动
- `inherit`: 从父级继承来clear的值
##### 9.2.3 例子
```
<!--html-->
<div id="container">
<div id="div1"></div>
<div id="div2"></div>
<div id="div3"></div>
<div id="clear">clear float</div>
</div>
/*css*/
#div1{
    width: 100px;
    height: 100px;
    background-color:red;
    float:left;
}
#div2{
    width: 100px;
    height: 100px;
    background-color:blue;
    float:left;
}
#div3{
    width: 100px;
    height: 100px;
    background-color:green;
    float: left;
}
#container{
    width: 500px;
    height: 300px;
    background-color: cornflowerblue;
}
#clear{
    clear: left;
}
```
### 10. 盒子模型
#### 10.1 盒子模型概念
盒子模型的内容范围包括： <br>
- `margin`: 外边距
- `border`: 边框
- `padding`: 内边距
- `content`: 内容
#### 10.2 内边距
##### 10.2.1 定义
`padding`控制着元素内容与`border`之间的间隙大小
##### 10.2.2 属性
- `padding`: 设置所有边距
- `padding-bottom`: 设置底边距
- `padding-left`: 设置左边距
- `padding-right`: 设置右边距
- `padding-top`: 设置上边距 <br/>
注意：如果不想每次都要分别声明`padding-bottom`，`padding-left`，`padding-right`，`padding-top`属性，<br/>
可以把他们汇总在`padding`属性里面声明：
`padding: 10px 20px 10px 20px` <br/>
这四个值按顺时针排序：上，右，下，左。
#### 10.3 边框
##### 10.3.1 定义
可以创建出效果出色的边框，并可以应于任何元素
##### 10.3.2 样式
- `border-style`: 定义了10个不同的非继承样式，包括`none` <br>
  `border-style: solid;`
##### 10.3.3 边框单边的样式
- `border-top-style`
- `border-left-style`
- `border-right-style`
- `border-bottom-style`
##### 10.3.4 边框的宽度
- `border-width`
#### 10.3.5 边框单边的宽度
- `border-top-width`
- `border-left-width`
- `border-right-width`
- `border-bottom-width`
##### 10.3.6 边框的颜色
- `border-color`
##### 10.3.7 边框单边的颜色
- `border-top-color`
- `border-left-color`
- `border-right-color`
- `border-bottom-color` 
##### 10.3.8 CSS边框
- `border-radius`: 圆角边框 <br>
   `border-radius: 20px;`
- `box-shadow`: 边框阴影 <br>
  `box-shadow: 10px 10px 5px royalblue;` //X轴偏移量，Y轴偏移量，模糊半径，颜色
- `border-image`: 边框图片 <br>
#### 10.4 外边距
##### 10.4.1 定义
围绕在内容边框的区域就是外边距，外边距默认为透明区域。外边距接受任何长度单位，百分数值 <br>
控制元素的边框与其他元素之间的距离
##### 10.4.2 属性
- `margin`: 设置所有边距
- `margin-bottom`: 设置底边距
- `margin-left`: 设置左边距
- `margin-right`: 设置有边距
- `margin-top`: 设置上边距 <br/>
每个方向的外边距值可以在`margin`属性里面汇总声明，<br/>
来代替分别声明`margin-top`，`margin-right`，`margin-bottom`和`margin-left`属性的方式，代码如下：<br/>
`margin: 10px 20px 10px 20px;`
这四个值按顺时针排序：上，右，下，左。
#### 10.5 外边距合并
##### 10.5.1 定义
外边距合并就是一个叠加的概念，以外边距大的为参照标准
### 11. CSS常用操作
#### 11.1 对齐
##### 11.1.1 使用margin属性进行水平对齐
```
margin:0px auto;
margin-left:auto;
margin-right:auto;
```
##### 11.1.2 使用position属性进行左右对齐
```
position:absolute;
right:0px;
```
##### 11.1.3 使用float属性进行左右对齐
`float:right;`
#### 11.2 尺寸 
- `line-height`: 设置行高，以此来设置行间距 <br>
  `line-height:200%；`
- `width`: 设置元素宽度
- `height`: 设置元素高度
- `max-width`: 设置元素最大宽度
- `min-width`: 设置元素最小宽度
- `max-height`: 设置元素最大高度
- `min-height`: 设置元素最小高度
#### 11.3 分类
- `clear`: 设置一个元素的侧面是否允许其他的浮动元素
- `cursor`: 规定当指向某元素之上时显示的指针类型
- `display`: 设置是否及如何显示元素，可以将`<li>`标签设置成一行 <br>
  `display: inline;`
- `float`: 定义元素在哪个方向浮动
- `position`: 把元素放置到一个静态的，相对的，绝对的，固定的位置
- `visibility`: 设置元素是否可见或不可见
#### 11.4 导航栏
##### 11.4.1 垂直导航栏
```
<!--html-->
<ul>
    <li><a href="#">苹果</a></li>
    <li><a href="#">橘子</a></li>
    <li><a href="#">香蕉</a></li>
</ul>
/*css*/
ul{
    list-style-type: none;
    margin: 0px;
    padding: 0px;
}
a:link,a:visited{
    text-decoration: none;
    display: block;
    background-color: cadetblue;
    color: red;
    width: 60px;
    text-align: center;
}
a:active,a:hover{
    color: blue;
}
```
##### 11.4.2 水平导航栏
```
ul{
    list-style-type: none;
    margin: 0px;
    padding: 0px;
}
a:link,a:visited{
    text-decoration: none;
    color: red;
    width: 60px;
    text-align: center;
}
a:active,a:hover{
    color: blue;
}
li{
    display: inline;
}
```
#### 11.5 图片
- `opacity`: 透明效果（0～1）
```
<!--html-->
<div class="image">
    <a href="#" target="_self">
    <img src="../../pic/cat.jpg" alt="cat" width="100px" height="100px">
    </a>
    <div class="note">可爱的猫咪</div>
</div>
/*css*/
img{
    margin: 5px;
    opacity: 0.5;
}
```
### 12. 选择器详解
#### 12.1 元素选择器
- 最常见的选择器，文档的元素就是最基本的选择器 <br>
  例如：`h1{},a{},p{}`
#### 12.2 选择器分组
- `h1,h1{}`
- `*{}`: 通配符
#### 12.3 类选择器详解
- 允许以一种独立与文档元素的方式来指定样式
  `.class{}`
- 结合元素选择器
  `a.class{}`
```
<!--html-->
<div class="div">hello</div>
<a class="div">hello</a>
/*css*/
a.div{color:red;}
```
- 多类选择器
  `.class.class{}`
```
<!--html-->
<p class="p1 p2">p1 p2</p>
/*css*/
.p1.p2{
    font-style:italic;
}
```
#### 12.4 ID选择器详解
- 类似于类选择器
`#id{}`
- 类选择器和ID选择器区别
ID只能在文档中使用一次，而类可以多次使用，ID选择器不能结合使用 <br/>
ID选择器的执行优先于类选择器。有时候它们声明的样式会意外的覆盖你的CSS样式。<br/>
当你需要保证你的CSS样式不受影响，你可以使用`!important`。<br/>
```
.pink-text {
    color: pink !important;
 }
```
当使用js时，需要用到`id` <br>
#### 12.5 属性选择器详解
- 简单属性选择 
 如：`[title]{}`
```
<head>
<style>
    [title]{
        color: brown;
    }
</style>
<head>
<body>
    <p title="">Hello</p>
</body>
```
- 根据具体属性值选择  <br>
除了选择拥有某些的元素，还可以进一步缩小选择范围，只选择有特定属性值的元素 <br>
例如：`a[href=""http://www.goole.co.jp]{}`
```
<head>
<meta charset="UTF-8">
<title>selector</title>
<link rel="stylesheet" type="text/css">
<style>
    [href]{
        font-size: 30px;
    }
</style>
</head>
<body>
  <a href="#">Hi</a>
</body>
```
- 属性和属性值必须完全匹配
```
[href="http://www.google.co.jp"]{
        font-size: 30px;
}
<a href="http://www.google.co.jp">Hi</a>
```
- 根据部分属性值选择
```
<head>
<style>
    [title~="title"]{
        font-size: 50px;
    }
</style>
</head>
<body>
  <p title="tit">Hello</p>
  <p title="title">Hello</p>
  <p title="t">Hello</p>
  <p title="title hello">Hello</p>
</body>
```
#### 12.6 后代选择器
后代选择器可以选择作为某元素后代的元素 <br>
```
<!--html-->
<p>my <strong>web<i>page</i></strong></p>
/*css*/
p strong i{
    color: red;
}
```
#### 12.7 子元素选择器
与后代选择器相比，子元素选择器只能选择作为某元素子元素的元素 <br>
`h1>strong{}`
#### 12.8 相邻兄弟选择器
可选择紧接在另一个元素后的元素，且二者有相同父元素 <br>
例如：`h1+p{}`
```
<!--html-->
<ul>
    <li>item1</li>
    <li>item2</li>
    <li>item3</li>
</ul>
/*css*/
li+li{
    color:red;
}
```
### 13. CSS动画
#### 13.1 2D，3D转换
##### 13.1.1 定义
通过CSS转换，对元素进行移动，缩放，转动，拉长或拉伸。转换是使元素改变形状，尺寸和位置的一种效果，可以使用2D，3D来转换元素 <br>
##### 13.1.2 2D转换方法
- `translate()`: 移动
```
<!--html-->
<div>hello div</div>
<br/>
<div class="div2">hello div2</div>
/*css*/
div{
    width: 100px;
    height: 100px;
    background-color: green;
}
.div2{
    tranceform:translate(100px,100px);
    -webkit-transform: translate(100px,100px);/*chrome safari*/
    -ms-transform: translate(100px,100px);/*ie*/
    -o-transform: translate(100px,100px);/*opera*/
    -moz-transform: translate(100px,100px);/*Firefox*/
}
```
- `rotate()`：旋转
```
.div2{
    _tranceform:rotate(200deg);_
    -webkit-transform: rotate(200deg);/*chrome safari*/
    -ms-transform: rotate(200deg);/*ie*/
    -o-transform: rotate(200deg);/*opera*/
    -moz-transform: rotate(200deg);/*Firefox*/
} 
```
- `scale()`：缩放 <br>
  `transform: scale(1,2);`
- `skew()`: 倾斜
  `transform:skew(20deg,20deg);`
- `matix()`
##### 13.1.3 3D转换方法
- `rotateX()` <br>
  `transform: rotateX(120deg);` <br>
- `rotateY()` <br>
  `transform: rotateY(120deg);`
#### 13.2 过渡
##### 13.2.1 定义
通过使用CSS3可以给元素添加一些效果
##### 13.2.2 特性
CSS3过渡是元素从一种样式转换成另一种样式 <br>
动画效果的CSS <br>
动画执行的时间 <br>
##### 13.2.3 属性
- `transition`: 设置四个过渡属性
- `transition-property`: 过渡的名称
- `transition-duration`: 过渡效果花费的时间
- `transition-timing-function`: 过渡效果的时间曲线
- `transition-delay`: 过渡延时开始时间
##### 13.2.4 例子
```
div{
    width: 100px;
    height: 100px;
    background-color: green;
    transition: width 20s,height 20s,transform 100s;
    transition-delay: 2s;
}
div:hover{
    width: 200px;
    height: 200px;
    transform: rotate(360deg);
}
```
#### 13.3 动画
##### 13.3.1 定义
通过CSS3，可以进行创建动画
##### 13.3.2 CSS3的动画需要遵循@keyframes规则
规定动画的时长 <br>
规定动画的名称 <br>
##### 13.3.3 例子
```
div{
    width: 100px;
    height: 100px;
    background-color: green;
    position: relative;
    animation: anim 5s infinite alternate;
}
@keyframes anim{
    0%{background: red;left:0px;top:0px}
    25%{background: green;left:200px;top:0px}
    50%{background: darkcyan;left:200px;top:200px}
    75%{background: indianred;left: 0px;top:200px}
    100%{background: red;left:0px;top:0px}
}
```
#### 13.4 多列
##### 13.4.1 定义
在CSS3中，可以创建多列来对文本或者区域进行布局
##### 13.4.2 属性
- `column-count`: 分列的数量
- `column-gap`: 每一列中间所间隔的距离
- `column-rule`: 每一列之间间隔的一条线及其颜色
##### 13.4.3 例子
```
.div1{
    column-count: 4;
    column-gap: 50px;
    column-rule: 2px outset red; //宽度 线条类型 颜色
}
```
### 14. CSS的自定义变量
#### 14.1 定义变量
创建一个CSS变量，你只需要在变量名前添加两个破折号，并为其赋值：<br/>
`--penguin-skin: gray;`
#### 14.2 引用变量
创建变量后，CSS属性可以通过引用变量名来使用它的值 <br/>
```
<style>
  .penguin {
     --penguin-skin: black;
   }
  .penguin-top {
     background: var(--penguin-skin);
   }
  .penguin-bottom {
     background: var(--penguin-skin);
   }
</style>
```
#### 14.3 给CSS变量附加回退值
如果使用不支持CSS变量的旧浏览器或者设备不支持设置的变量值，可以写成如下形式：<br/>
```
<style>
  .penguin {
     --penguin-skin: gray;
   }
  .penguin-top {
     background: var(--penguin-skin,black);
   }
  .penguin-bottom {
     background: var(--penguin-skin,black);
   }
</style>
```
#### 14.4 层级CSS变量
CSS变量通常会定义在`:root`元素里。<br/>
在`:root`创建的变量，在整个网页里面都能生效。<br/>
```
:root {
    --penguin-belly: pink;
  }
```
#### 14.5 更改特定区域的变量
```
<style>
  :root {
    --penguin-belly: pink;
  }
  .penguin {
    --penguin-belly: white;
  }
</style>
```
#### 14.6 使用媒体查询更改变量
CSS 变量可以简化媒体查询的方式。<br/>
例如，当屏幕小于或大于媒体查询所设置的值，通过改变变量的值，那么应用了变量的元素样式都会得到响应修改。<br/>
```
<style>
  :root {
    --penguin-size: 300px;
    --penguin-skin: gray;
  }
  
  @media (max-width: 350px) {
    :root {
     --penguin-size: 200px;
     --penguin-skin: black; 
    }
  }
</style> 
```

 


