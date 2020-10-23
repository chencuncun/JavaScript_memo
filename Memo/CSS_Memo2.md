# CSS 笔记重点

## 1.选择器详解
### 1.1 常用选择器
#### 1.1.1 元素选择器
- 作用：根据标签名来选中指定的元素
- 语法：`标签名{}`
- 例子：`p{}` `h1{}` `div{}`
#### 1.1.2 id选择器
- 作用：根据元素的id属性值选中一个元素
- 语法：`#id属性值{}`
- 例子：`#box{}` `#red{}`
#### 1.1.3 class选择器
- 作用：根据元素的class属性值选中一组元素
- 语法：`.class属性值`
- 例子：`.blue{}` 
- 补充：`class`是一个标签的属性，它和`id`类似，不同的是`class`可以重复使用。可以通过`class`属性来为元素分组，可以同时为一个元素指定多个`class`属性
#### 1.1.4 通配选择器
- 作用：选中页面中的所有元素
- 语法：`*{}`

### 1.2 复合选择器
#### 1.2.1 交集选择器
- 作用：选中同时符合多个条件的元素
- 语法：`选择器1选择器2选择器n{}`
- 注意：交集选择器中如果有元素选择器，必须使用元素选择器开头
```
//将class为red的div元素的字体大小设置为30px 
<style> 
    div.red{
        font-size: 30px;
    }
</style> 
<div class="red">我是div元素</div>
<p class="red">我是p元素</p>
```
#### 1.2.2 并集选择器（选择器分组）
- 作用：同时选择多个选择器对应的元素
- 语法：`选择器1，选择器2，选择器{}`
```
//将h1和span元素同时设置为30px 
<style> 
    h1,span{
        font-size: 30px;
    }
</style> 
<h1>我是h1标签</h1>
<span>我是span元素</span>
```

### 1.3 关系选择器
#### 1.3.1 父元素
- 定义：直接包含子元素的元素
#### 1.3.2 子元素选择器
- 定义：直接被父元素包含的元素
- 作用：选中指定父元素的指定子元素
- 语法：`父元素 > 子元素`
- 例子：`div.box > span{}`
#### 1.3.3 祖先元素
- 定义：直接或间接包含后代元素的元素
- 注意：一个元素的父元素也是它的祖先元素
#### 1.3.4 后代元素选择器
- 定义：直接或间接被祖先元素包含的元素
- 注意：子元素也是后代元素
- 作用：选中指定元素内的指定后代元素
- 语法：`祖先 后代`
- 例子：`div span{}`
#### 1.3.5 兄弟元素选择器
- 定义：拥有相同父元素的元素
- 语法：`前一个+后一个`
- 例子：`p+span{}` ：//选择p后面的span元素
- 追加语法：`兄~弟`
- 追加语法的例子：`p~span{}` ：//选择p后面所有的兄弟
 
### 1.4. 属性选择器
#### 1.4.1 属性选择器
对带有指定属性的HTML元素设置样式
#### 1.4.2 属性和值选择器
- [属性名]：选择含有指定属性的元素
```
<style type="text/css">
    [title]{
        color: chocolate;
    }
</style>  
<p title="t">属性选择器</p>
<p title="te">属性和值选择器</p>
```
- [属性名=属性值]：选择含有指定属性和属性值的元素
```
<style type="text/css">
    [title=te]{
        color: darkcyan;
    }
</style>  
<p title="t">属性选择器</p>
<p title="te">属性和值选择器</p>
```
- [属性名^=属性值]：选择属性值以指定值开头的元素
```
<style>
    p[title^=abc]{
        color:orange;    
    }
</style>
<body>
    <p title="abc">少小离家老大回</p>
    <p title="abcdef">乡音无改鬓毛衰</p>
    <p title="hello">儿童相见不相识</p>
</body>
```
- [属性名$=属性值]：选择属性值以指定值结尾的元素
```
<style>
    p[title$=abc]{
        color:orange;    
    }
</style>
<body>
    <p title="abc">少小离家老大回</p>
    <p title="abcdef">乡音无改鬓毛衰</p>
    <p title="helloabc">儿童相见不相识</p>
</body>
```
- [属性名*=属性值]：选择属性值中含有某值的元素
```
<style>
    p[title*=abc]{
        color:orange;    
    }
</style>
<body>
    <p title="abc">少小离家老大回</p>
    <p title="abcdef">乡音无改鬓毛衰</p>
    <p title="helloabc">儿童相见不相识</p>
</body>
```

### 1.5 伪类选择器
定义：不存在的类，特殊的类。用来描述一个元素的特殊状态。<br/>
比如：第一个子元素，被点击的元素，鼠标移入的元素。。。<br/>
一般情况下都是以`：`开头 <br/>
#### 1.5.1 常用伪类
- `:first-child`：第一个子元素
```
<style>
    ul > li:first-child{
        color:red;
     }
</style>
<body>
    <ul>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>    
</body>
```
- `:last-child`：最后一个子元素
```
<style>
    ul > li:last-child{
        color:red;
     }
</style>
<body>
    <ul>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>    
</body>
```
- `:nth-child()`：选中第n个子元素 <br/>
特殊值`n`：`n`的范围0到正无穷 <br/>
`2n`或`even`表示选中偶数位的元素 <br/>
`2n+1`或`odd`表示选中奇数位的元素 <br/>

```
<style> 
    ul > li:nth-child(2){
        color:red;
     }
</style>
<body>
    <ul>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>    
</body>
```
- `:first-of-type`
- `:last-of-type`
- `:nth-of-type()` <br/>
以上这几个伪类的功能与`child`类似，不同点是在同类型元素中进行排序 <br/>
- `:not()`：否定伪类 <br/>
将符合条件的元素从选择器中去除
```
<style>
    ul>li:not(:nth-of-type(3)){
        color: darkcyan;
    }
</style>
</head>
<body>
    <ul>
        <span>我是span元素</span>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>
</body>
```
#### 1.5.2 链接有关的伪类
- `a:link`: 未被访问的链接 <br/>
```
a:link{
    color: red;
}
```
- `a:visited`: 已访问的链接 <br/>
为了保护隐私，`a:visited`这个伪类只能修改链接的颜色 <br/>
```
a:visited{
    color: orange;
}
```
- `a:hover`: 鼠标指针位于链接的上方 <br/>
```
a:hover{
    color: blue;
}
```
- `a:active`: 链接被点击的时刻 <br/>
```
a:active{
    color: green;
}
```
### 1.6 伪元素选择器
表示页面中一些特殊的并不真实的存在的元素（特殊的位置）<br/>
伪元素使用`::`开头 <br/>
- `::first-letter` 表示第一个字母 <br/>
```
//将p里面的首字母大小改为50px
<head>
    <style>
        p::first-letter{
            font-size: 50px;
        }
    </style>
</head>
<body>
    <p>
        This is a page for studying html.
    </p>
</body>
```
- `::first-line` 表示第一行
```
p::first-line{
    background-color: yellow;
}
```
- `::selection` 表示选中的内容
```
//当鼠标选中某区域，某区域变为绿色
p::selection{
    background-color: green;
}
```
- `::before` 元素的开始位置 与`::after`元素的结束位置 <br/>
`::before`和`::after`必须结合`content`属性来使用，因为是在css中添加的内容，所以不能被选中。
```
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        p::before{
            content: 'abc';
            color: red;
        }
        p::after{
            content: 'xyz';
            color: green;
        }
    </style>
</head>
<body>
    <p>
        This is a page for studying html.
    </p>
</body>
```
## 2. 布局
### 2.1 文档流
- 网页是一个多层的结构，一层叠加一层
- 通过CSS可以分别为每一层来设置样式
- 作为用户来讲只能看到最顶上一层
- 这些层中，最底下的一层成为文档流，文档流是网页的基础。我们所创建的元素默认都是在文档流中进行排列
- 对于我们来说元素主要有两个状态：在文档流中，不在文档流中
### 2.2 元素状态详解
#### 2.2.1 在文档流中
- 块元素
  - 块元素会在页面中独占一行（自上而下垂直排列）
  - 默认宽度是父元素的全部（会把父元素撑满）
  - 默认高度是被内容撑开（子元素）
```
//即使将box1和box2的宽度设为100px，box2也不会和box1拼接在一起
<head>
<style>
        .box1{
            width: 100px;
            background-color: yellow;
        }
        .box2{
            width: 100px;
            background-color: green;
        }
    </style>
</head>
<body>
<div class="box1">我是div1</div>
<div class="box2">我是div2</div>
</body>
```
- 行内元素
  - 行内元素不会独占页面的一行，只占自身的大小
  - 行内元素在页面中从左向右水平排列。如果一行之中不能容纳所有的行内元素，则会换到第二行继续自左向右排列
  - 行内元素的默认宽度和高度都是被内容撑开
#### 2.2.2 不在文档流中（脱离文档流）
## 3. 盒模型
### 3.1 定义
- CSS将页面中的所有元素都设置为了一个矩形的盒子
- 将元素设置为矩形的盒子后，对页面的布局就变成将不同的盒子摆放到不同的位置
- 每个盒子都由以下几个部分组成
  - 内容区：`content`
  - 内边距：`padding`
  - 边框：`border`
  - 外边距：`margin`
### 3.2 盒子组成详解
#### 3.2.1 内容区：`content`
元素中的所有的子元素和文本内容都在内容区中排列 <br/>
内容区的大小由`width`和`height`两个属性来设置 <br/>
- 内容区的宽度：`width`
- 内容区的高度：`height`
```
.box1{
    width:200px;
    height:200px;
    background-color:green;
}
```
#### 3.2.2 边框：`border`
边框属于盒子边缘，边框里边属于盒子内部，出了边框就是盒子的外部 <br/>
边框的大小会影响到整个盒子的大小。要设置边框，需要至少设置三个样式 <br/>
- 边框的宽度：`border-width` 
    - 默认值：一般为3个像素
    - 值的情况
      - 四个值：上，右，下，左
      - 三个值：上，左右，下
      - 两个值：上下，左右
      - 一个值：上下左右
```
.box1{
    border-width:10px 20px; //上下10px，左右20px
}
```      
   - 单独指定某一个边的宽度：`border-xxx-width`
     - `border-top-width`
     - `border-bottom-width`
     - `border-left-width`
     - `border-right-width`
     
- 边框的颜色：`border-color`：可以分别指定四个边的边框，规则和`border-width`一样 <br/>
注意：`border-color`也可以省略不写，如果省略了则自动使用`color`颜色值 <br/>
`border-color:orange red yellow green`
- 边框的样式：`border-style`：可以分别指定四个边的样式，规则和`border-width`一样
  - `solid`：表示实线
  - `dotted`：点状虚线
  - `dashed`：虚线
  - `double`：双线
```
.box1{
    border-width:10px;
    border-color:orange;
    border-style:solid;
}
```
- `border`简写属性：通过该属性可以同时设置边框所有的相关样式，并且没有顺序要求 <br/>
`border:10px orange solid;`
- `border-xxx`：每个边框单独设置样式
  - `border-top:10px orange solid;`
  - `border-bottom:10px orange solid;`
  - `border-left:10px orange solid;`
  - `border-right:10px orange solid;`
```
border:10px red solid;
border-right:none;
```
#### 3.2.3 内边距：`padding`
内容区和边框之间的距离是内边距，一共有四个方向的内边距。<br/>
内边距的设置会影响到盒子的大小，同时背景颜色会延伸到内边距上 <br/>
一个盒子的可见框的大小，由内容区，内边距和边框加到一起计算。 <br/>
- 属性
  - `padding-top`
  - `padding-right`
  - `padding-bottom`
  - `padding-left`
- `padding`内边距的简写属性，可以同时指定四个方向的内边距 <br/>
`padding: 10px 20px 30px 40px;`
  - 值的情况
    - 四个值：上，右，下，左
    - 三个值：上，左右，下
    - 两个值：上下，左右
    - 一个值：上下左右
#### 3.2.4 外边距：`margin`
外边距不会影响盒子可见框的大小，但是外边距会影响盒子的位置。<br/>
`margin`会影响到盒子实际占用空间。<br/>
一共有四个方向的外边距 <br/>
- 属性
  - `margin-top`：上外边距，设置一个正值，元素会向下移动。正值都会往相反的方向移动。
  - `margin-right`：由浏览器自动调整
  - `margin-bottom`：下边距，设置一个正值，其下边的元素会向下移动。
  - `margin-left`：左外边距，设置一个正值，元素会向右移动。
- `margin`也可以设置负值，如果是负值则元素会向相反的方向移动。 <br/>
注意：`margin-top`和`margin-left`是移动自己，`margin-right`和`margin-bottom`是挤别人。<br/>
元素在页面中是按照自左向右的顺序排列的，所以默认情况下，我们设置的左和上边距则会移动元素自身，而设置下和右边距会移动其他元素。<br/>
- `margin`的简写属性 <br/>
`margin`可以同时设置四个方向的外边距，用法和`padding`一样 <br/>
`margin: 10px 20px 30px 40px;`
### 3.3 盒子的水平布局
元素在其父元素中水平方向的位置由以下几个属性共同决定 <br/>
- `margin-left`
- `border-left`
- `padding-left`
- `width`
- `padding-right`
- `border-right`
- `margin-right`
一个元素在其父元素中，水平布局必须要满足以下的等式 ：<br/>
`margin-left` + `border-left` + `padding-left` + `width` + `padding-right` + `border-right` + `margin-right` <br/>
以上等式必须满足，如果相加结果使等式不成立，则称为过渡约束，则等式会被浏览器自动调整  <br/>
调整的情况：如果这7个值中没有`auto`的情况，则浏览器会自动调整`margin-right`值以确保等式成立 <br/>
这7个值中有3个值可以设置为`auto` <br/>
- `width`：默认值为`auto`
- `margin-left`
- `margin-right`
如果某个值为`auto`，则会自动调整为`auto`的那个值以确保等式成立 <br/>
如果将一个宽度和一个外边距设置为`auto`，则宽度会调到最大 <br/>
如果将三个值都设置为`auto`，则外边距都是0，宽度最大 <br/>
如果将两个外边距设置为`auto`，宽度固定值，则会将外边距设置为相同的值，所以经常利用这个特点来使一个元素在其父元素中水平居中 <br/>
例子：<br/>
```
width: xxx px;
margin: 0 auto;
```
### 3.4 盒子的垂直方向布局
- 父元素设定了高度就是其高度
```
.outer{
    background-color: green;
    height: 600px;
}
```
- 父元素不设定高度，其高度是被子元素撑开的高度
子元素是在父元素的内容区中排列的，如果子元素的大小超过了父元素，则子元素会从父元素中溢出 <br/>
使用`overflow`属性来设置父元素如何处理溢出的子元素 <br/>
  - 可选值
    - `visible`：默认值 子元素会从父元素中溢出，在父元素外部的位置显示
    - `hidden`：溢出内容将会被裁剪不会显示
    - `scroll`：生成两个滚动条，通过滚动条来查看完整的内容
    - `auto`：根据需要生成滚动条 <br/>
  `overflow: auto;` //更灵活
  - `overflow-x`和`overflow-y`：单独处理x轴方向和单独处理y轴方向
### 3.5 外边距的折叠
相邻的垂直方向外边距会发生重叠现象 <br/>
- 兄弟元素
  - 兄弟元素间的相邻垂直外边距会取两者之间的较大值（两者都是正值）
  - 如果相邻的外边距一正一负，则取两者的和
  - 如果相邻的外边距都是负值，则取两者中绝对值较大的
  - 兄弟元素之间的外边距的重叠，对于开发是有利的，所以我们不需要处理
- 父子元素
  - 父子元素间相邻外边距，子元素的会传递给父元素（上外边距）
  - 父子外边距的折叠会影响到页面布局，必须要进行处理  
### 3.6 行内元素的盒模型
行内元素不支持设置宽度和高度，所以给行内元素设置`width`和`height`没有效果。<br/>
行内元素可以设置`padding`，垂直方向`padding`不会影响页面的布局。<br/>
行内元素可以设置`border`，垂直方向的`border`不会影响页面的布局。<br/>
行内元素可以设置`margin`，垂直方向的`margin`不会影响布局。<br/>
- `display`: 用来设置元素显示的类型 <br/>
可选值：<br/>
  - `inline`： 将元素设置为行内元素
  - `block`： 将元素设置为块元素 
  - `inline-block`：将元素设置为行内块元素：行内块，既可以设置宽度和高度又不会独占一行
  - `table`：将元素设置为一个表格
  - `none`：元素不在页面中显示
- `visibility`：用来设置元素的显示状态 <br/>
可选值：<br/>
  - `visible`：默认值，元素在页面中正常显示
  - `hidden`：元素在页面中隐藏不显示，但是依然占据页面的位置
### 3.7 默认样式
#### 3.7.1 介绍
通常情况下，浏览器都会为元素设置一些默认样式。默认样式的存在会影响到页面的布局。<br/>
通常情况下，编写网页时必须要去除浏览器的默认样式(PC端的页面)。<br/>
#### 3.7.2 去除浏览器默认样式
- 小demo的情况下
```
*{
    margin: 0;
    padding: 0;
}
```
以上方法去除浏览器默认样式，可能会有残余。<br/>
- `reset.css`：直接去除了浏览器的默认样式 <br/>
<https://meyerweb.com/eric/tools/css/reset/> <br/>
- `normalize.css`：对默认样式进行了统一 <br/>
<https://necolas.github.io/normalize.css/> <br/>

### 3.8 盒子大小
默认情况下，盒子可见框的大小由内容区，内边距和边框共同决定 <br/>
- `box-sizing`：用来设置盒子尺寸的计算方式（设置`width`和`height`的作用）
可选值 <br/>
  - `content-box`： 默认值，宽度和高度用来设置内容区的大小
  - `border-box`：宽度和高度用来设置整个盒子可见框的大小（`width`和`height`指的是内容区和边框的总大小）
```
/* box1的大小是100x100px */
.box1{
    width: 100px;
    height: 100px;
    background-color: #bfa;
    padding: 10px;
    border: 10px red solid;
    box-sizing: border-box;
    }
```
### 3.9 轮廓阴影和圆角
- `outline`：用来设置元素的轮廓线，用法和`border`一样。不同点是轮廓不会影响到可见框的布局。
- `box-shadow`：用来设置元素的阴影效果，阴影不会影响页面的布局。默认情况下，阴影位于元素的正下方。
  - 第一个值：水平偏移量。设置阴影的水平位置，正值向右移动，负值向左移动。
  - 第二个值：垂直偏移量。设置阴影的垂直位置，正值向下移动，负值向上移动。
  - 第三个值：阴影的模糊半径，值越大越模糊
  - 第四个值：阴影的颜色 <br/>
`box-shadow: 20px 20px 10px rgba(0,0,0,.3);` 
- `border-radius`：用来设置圆角，圆角设置的是圆的半径大小。可以分别指定四个角的圆角。
  - 四个值：左上 右上 右下 左下 `border-radius:10px 20px 30px 40px;`
  - 三个值：左上 右上/左下 右下
  - 两个值：左上/右下 右上/左下
  - 一个值：左上/右上/右下/左下
  `border-radius: 20px / 40px;` 左上/左下：20px 右上/右下：40px 
  `border-radius: 50%;` 将元素设置为一个圆形
  - `border-top-left-radius`
  - `border-top-right-radius`
  - `border-bottom-left-radius`
  - `border-bottom-left-radius`
```
/* 左上角水平半径50px，垂直半径100px */
border-top-left-radius:50px 100px;
```  
## 4. 浮动 `float`
设置元素的浮动通过浮动可以使一个元素向其父元素的左侧或右侧移动。<br/>
### 4.1 简介
- 可选值
  - `none`：默认值，元素不浮动
  - `left`：元素向左浮动
  - `right`：元素向右浮动
- 注意
  - 元素设置浮动后，水平布局的等式便可以不需要强制成立。
  - 元素设置浮动后，会完全从文档流中脱离，不在占用文档流的位置，所以元素下边的还在文档流中的元素会自动向上移动。
- 特点
  - 浮动元素会完全脱离文档流，不在占据文档流中的位置
  - 设置浮动以后，元素会向父元素的左侧或右侧移动
  - 浮动元素默认不会从父元素中移出
  - 浮动元素向左或向右移动时，不会超过它前边的其他浮动元素
  - 如果浮动元素的上边是一个没有浮动的块元素，则浮动元素无法上移
  - 浮动元素不会超过它上边的浮动的兄弟元素，最多和它一样高
- 总结
  - 浮动主要作用是让页面中的元素可以水平排列
  - 通过浮动可以制作一些水平方向的布局
### 4.2 特点
浮动元素不会覆盖文字，文字会自动环绕在浮动元素的周围，所以可以利用浮动来设置文字环绕图片的效果。<br/> 
元素设置浮动以后，将会从文档流中脱离。从文档流中脱离后，元素的一些特点也会发生变化。<br/>
- 块元素
  - 块元素不在独占页面的一行
  - 脱离文档流以后，块元素的宽度和高度默认都会被内容撑开
- 行内元素
  - 行内元素脱离文档流后以后，特点和块元素一样。也可以对其进行宽和高的设定
- 提示
  - 脱离文档流以后，就不需要再区分块和行内元素了
### 4.3 问题
#### 4.3.1 高度塌陷
在浮动布局中，父元素的高度默认是被子元素撑开的，当子元素浮动后，其会完全脱离文档流，<br/>
子元素从文档中脱离将会无法撑起父元素的高度，导致父元素的高度丢失。<br/>
父元素高度丢失以后，其下的元素会自动上移，导致页面的布局混乱。<br/>
所以高度塌陷是浮动布局中比较常见的一个问题，这个问题我们必须要进行处理！ <br/>
#### 4.3.2 解决方法1：BFC
##### 4.3.2.1 定义
BFC(Block Formatting Context)：块级格式化环境 <br/>
- BFC是一个CSS中的一个隐含的属性，可以为一个元素开启BFC
- 开启BFC该元素会变成一个独立的布局区域
##### 4.3.2.2 开启BFC后的特点
- 开启BFC的元素不会被浮动元素所覆盖
```  
/* 解决box2被box1覆盖的问题 */
<style>
    .box1{
        width: 200px;
        height: 200px;
        float: left;
        background-color: rosybrown;
    }
    .box2{
        width: 200px;
        height: 200px;
        <!-- 开启BFC -->
        overflow: hidden;
        background-color: royalblue;
    }
</style> 
<body>
    <div class="box1"></div>
    <div class="box2"></div>
</body>    
```
- 开启BFC的元素子元素和父元素外边距不会重叠
```
/* 避免父元素外边距跟着子元素外边距下移的问题 */
<style>
    .box1{
        width: 200px;
        height: 200px;
        /* 将父元素开启BFC */
        overflow: hidden;
        background-color: rosybrown;
    }
    .box2{
        width: 100px;
        height: 100px;
        margin-top: 100px;
        background-color: royalblue;
    }
</style> 
<body>
    <div class="box1">
        <div class="box2"></div>
    </div>
</body>
```
- 开启BFC的元素可以包含浮动的子元素
##### 4.3.2.3 开启BFC的方式
- 设置元素的浮动(不推荐)
`float: left;`
- 将元素设置为行内块元素(不推荐)
`display: inline-block;`
- 将元素的`overflow`设置为一个非`visible`的值
  - 常用方式：为元素设置`overflow：hidden;`开启其BFC，以使其可以包含浮动元素
### 4.3.3 解决方法2：`clear`
- 作用：清除浮动元素对当前元素所产生的影响
- 可选值
  - `left`：清除左侧浮动元素对当前元素的影响
```
<style>
    div{
        font-size: 50px;
    }
    .box1{
        width: 200px;
        height: 200px;
        float:left;
        background-color: royalblue;
    }
    .box2{
        width: 200px;
        height: 200px;
        /* 清除左浮动，使其不被box1覆盖 */
        clear: left;
        background-color: saddlebrown;
    }
</style>
<body>
    <div class="box1">1</div>
    <div class="box2">2</div>
</body>
```
  - `right`：清除右侧浮动元素对当前元素的影响
  - `both`：清除两侧中最大影响的那一侧
```  
/* box1是被box3撑开，box3清除了浮动的影响，所以box3一直位于box2的下方 */
<style>
    .box1{
        border: 10px red solid;
    }
    .box2{
        width: 100px;
        height: 300px;
        background-color: saddlebrown;
        float: left;
    }
    .box3{
        /* 清除浮动对其的影响 */
        clear: both;
    }
</style>
<body>
    <div class="box1">
        <div class="box2"></div>
        <div class="box3"></div>
    </div>
</body>
```
- 原理
  - 设置清除浮动以后，浏览器会自动为元素添加一个外边距，以使其位置不受其他元素的影响  

### 4.3.4 解决方法3：`after`
使用`after`伪类解决高度塌陷
```
<style>
    .box1{
        border: 10px red solid;
    }
    .box2{
        width: 100px;
        height: 300px;
        background-color: saddlebrown;
        float: left;
    }
    /* 添加一个伪类来将父类的内容撑开 */
    .box1::after{
        content: '';
        display: block;
        clear: both;
    }
</style>
<body>
    <div class="box1">
        <div class="box2"></div>
    </div>
</body>
```
### 4.3.5 追加：`clearfix`
可以同时解决高度塌陷和外边距重叠的问题。
```
<head>
    <meta charset="UTF-8">
    <title>clearfix</title>
    <style>
        .box1{
            width:200px;
            height: 200px;
            /* overflow: hidden; */
            background-color: seagreen;
            border: 10px red solid;
        }
        .box2{
            width: 100px;
            height: 100px;
            background-color: sienna;
            margin-top: 100px;
        }
        /* 同时解决高度塌陷和外边距重叠 */
        .clearfix::before,
        .clearfix::after{
            content:'';
            display: table;
            clear: both;
        }
    </style>
</head>
<body>
    <div class= "box1 clearfix">
        <div class="box2"></div>
    </div>
</body>
</html>
```
## 5. 定位：`position`
定位是一种更加高级的布局手段，通过定位可以将元素摆放到页面的任意位置。使用`position`属性来设置定位。
## 5.1 可选值
- `static`：默认值，元素是静止的没有开启定位
- `relative`：开启元素的相对定位
- `absolute`：开启元素的绝对定位 
- `fixed`：开启元素的固定定位
- `sticky`：开启元素的粘滞定位
## 5.2 详细
### 5.2.1 相对定位：`relative`
当元素的`position`属性值设置为`relative`时则开启了元素的相对定位 <br/>
- 特点：
  - 元素开启相对定位以后，如果不设置偏移量元素不会发生任何变化
  - 相对定位是参照于元素在文档流中的原始位置进行定位的
  - 相对定位会提升元素的层级
  - 相对定位不会使元素脱离文档流
  - 相对定位不会改变元素的性质块还是块，行内还是行内
- 偏移量(offset)：当元素开启了定位以后，可以通过偏移量来设置元素的位置
  - `top`：定位元素和定位位置上边的距离
  - `bottom`：定位元素和定位位置下边的距离 <br/>
    - 定位元素垂直方向的位置由`top`和`bottom`两个属性来控制，通常情况下我们只会使用其中之一。<br/>
    - `top`值越大，定位元素越向下移动
    - `bottom`值越大，定位元素越向上移动
  - `left`：定位元素和定位位置的左侧距离
  - `right`：定位元素水平方向的位置由`left`和`right`两个属性控制，通常情况下只会使用一个。`left`越大元素越靠右，`right`越大元素越靠左。
```
<head>
     <style>
        body{
            font-size:60px;
        }
        .box1{
            width: 200px;
            height: 200px;
            background-color: sienna;
        }
        .box2{
            width: 200px;
            height: 200px;
            background-color: slateblue;
            /* 将box2往左，往上移动 */
            position:relative;
            left:200px;
            top:-200px;
        }
        .box3{
            width: 200px;
            height: 200px;
            background-color: steelblue;
        }
    </style>
</head>
<body>
    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div>
</body>
```
### 5.2.2 绝对定位：`absolute`
当元素的`position`属性值设为`absolute`时，则开启了元素的绝对定位  <br/>
- 特点：<br/>
  - 开启绝对定位后，如果不设置偏移量元素的位置不会发生变化
  - 开启绝对定位后，元素会从文档流中脱离
  - 绝对定位会改变元素的性质，行内变成块，块的宽高被内容撑开
  - 绝对定位会使元素提升一个层级
  - 绝对定位元素是相对于其包含块进行定位的
- 包含块 <br/>
  - 正常情况下：包含块就是离当前元素最近的祖先块元素
    `<div><div></div><div>`
    `<div><span><em>hello</em</span></div>`
  - 绝对定位的包含块：包含块就是离它最近的开启了定位的祖先元素。如果所有的祖先元素都没有开启定位，则根元素就是它的包含块。
  - `html`：根元素，初始包含块
- 偏移量：参考相对定位
- 绝对定位元素的布局
  - 水平布局 <br/>
  `left + margin-left + border-left + padding-left + width + padding-right + border-right + margin-right + right = 包含块的内容区的宽度`
  - 开启绝对定位后 <br/>
  水平方向的布局等式需要添加`left`和`right`两个值 <br/>
  此时规则和之前一样只是添加了两个值，当发生过渡约束时：<br/>
    - 如果9个值中没有`auto`则自动调整`right`值，以使等式满足。
    - 如果有`auto`，则自动调整`auto`的值，以使等式满足。
    - 可设置`auto`的值：`margin`，`width`，`left`，`right`
    - 因为`left`和`right`的值默认是`auto`，所以如果不指定`left`和`right`，则等式不满足时，会自动调整这两个值。
```
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .box1{
            width: 500px;
            height: 500px;
            background-color: sienna;
            position: relative;
        }
        .box2{
            width: 100px;
            height: 100px;
            background-color: slateblue;
            position:absolute;
            margin-left: auto;
            margin-right:auto;
            left:0px;
            right:0px;
        }
    </style>
</head>
<body>
    <div class="box1">
        <div class="box2"></div>
    </div>
</body>
```
  - 垂直布局 <br/>
  垂直方向布局的等式也必须满足：<br/>
  `top + margin-top/bottom + border-top/bottom + padding-top/bottom + height + bottom = 包含块的高度`
```
/* 将box2放置在box1的正中间 */
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box1{
            width: 500px;
            height: 500px;
            background-color: sienna;
            position: relative;
        }
        .box2{
            width: 100px;
            height: 100px;
            background-color: slateblue;
            position: absolute;
            margin-left: auto;
            margin-right: auto;
            margin-top: auto;
            margin-bottom: auto;
            left: 0px;
            right: 0px;
            top: 0px;
            bottom: 0px;
        }
    </style>
</head>
<body>
    <div class="box1">
        <div class="box2"></div>
    </div>
</body>
```
### 5.2.3 固定定位：`fixed`
将元素的`position`属性设置为`fixed`则开启了元素的固定定位<br/>
固定定位也是一种绝对定位，所以固定定位的大部分特点都和绝对定位一样。<br/>
唯一不同的是固定定位永远参照于浏览器的视口进行定位，固定定位的元素不会随网页的滚动条而滚动。
### 5.2.4 粘性定位：`sticky`
当元素的`position`属性设置为`sticky`时则开启了元素的粘滞定位。<br/>
粘滞定位和相对定位的特点基本一致，不同的是粘滞定位可以在元素到达某个位置时将其固定。<br>
```
/* 将导航栏在滚动条拖到离顶部10px的位置固定 */
.nav{
    position: sticky; 
    top: 10px;
}
```
## 5.3 元素的层级：`z-index`
对于开启了定位的元素，可以通过`z-index`属性来指定元素的层级 <br/>
`z-index`需要一个整数作为参数，值越大元素的层级越高，元素的层级越高越优先显示<br/>
如果元素的层级一样，则优先显示靠下的元素。<br/>
祖先元素的层级再高也不会盖住后代元素。<br/>
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box1{
            width: 100px;
            height: 100px;
            background-color: sienna;
            position: absolute;
            z-index: 1;
        }
        .box2{
            width: 100px;
            height: 100px;
            background-color: rgba(255,0,0,.3);
            position: absolute;
            top: 50px;
            left: 50px;
            z-index: 2;
        }
        .box3{
            width: 100px;
            height: 100px;
            background-color:teal;
            position: relative;
            top: 100px;
            left: 100px;
            z-index: 3;
        }
    </style>
</head>
<body>
    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div>
</body>
```
## 6. 字体
### 6.1 字体相关的样式
- `color`：用来设置字体颜色
- `font-size`：字体的大小
  - `em`：相对于当前元素的一个`font-size`
  - `rem`：相对于根元素的一个`font-size`
- `font-family`：字体族（字体的格式） <br/>
  可选值：<br/>
  - `serif`：衬线字体
  - `san-serif`：非衬线字体
  - `monospace`：等宽字体 <br/>
  指定字体的类别，浏览器会自动使用该类别下的字体 <br/>
  `font-family`可以同时指定多个字体，多个字体间使用`,`隔开，字体生效时优先使用第一个，第一个无法使用则使用第二个，依此类推。<br/>
  `font-family: Georgia, 'Times New Roman', Times, serif;`
  - `font-face`：可以将服务器中的字体直接提供给用户取使用 <br/>
    问题：<br/>
    - 加载速度
    - 版权  
    - 字体格式
```
@font-face{
    /*指定字体的名字*/
    font-family: 'myfont';
    /*服务器中字体的路径*/
    src: url('./font/ZCOOLXiaoWei-Regular.ttf');
}
p{
    font-family: myfont;
}
```
### 6.2 图标字体：`iconfont`
在网页中经常使用一些小图标，可以通过图片来引入图标，但是，图片大小本身比较大，并且非常的不灵活（比如：无法改颜色，大小设置比较麻烦等）<br/>
所以在使用图标时，可以将图标直接设置为字体，然后通过`font-face`的形式来对字体进行引入，这样即可通过使用字体的形式来使用图标。<br/>
#### 6.2.1 图标库1：fontawesome
- 下载地址：<https://fontawesome.com/>
    - 解压
    - 将css和webfonts移动到项目中，必须放到同一路径下
    - 将all.css引入网页中
    - 使用图标字体
      - 直接通过类名来使用图标字体：<br/>
      <https://www.runoob.com/font-awesome/fontawesome-tutorial.html>
      `<i class="fas fa-bell"></i>`
      `<i class="fab fa-accessible-icon"></i>`
#### 6.2.2 图标库2：runoob.com
- 网址：<https://www.runoob.com/font-awesome/fontawesome-reference.html>
- 将图标库引入网页中：<br/>
`<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">`
#### 6.2.2 图标库3：阿里图标库
网址：<https://www.iconfont.cn/>
### 6.3 图标字体的其他使用方式
#### 6.3.1 通过伪元素来设置图标字体
- 找到要设置图标的元素，通过`before`和`after`选中
- 在`content`中设置字体的编码
  - 编码网址（unicode的f开始四位）：<https://www.runoob.com/font-awesome/fontawesome-reference.html>
- 设置字体样式：参考本地`"../../fontawesome/css/all.css"文件`
  - fab
```
  font-family: 'Font Awesome 5 Brands';
  font-weight: 400;
```
  - fas
```
  font-family: 'Font Awesome 5 Free';
  font-weight: 900;
```
``` 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>icon_other</title>
    <link rel="stylesheet" href="../../fontawesome/css/all.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <style>
        li{
            list-style: none;
        }
        /* 给li标签前面添加剪刀手符号 */
        li::before{
            content:'\f209';
            font-family: 'Font Awesome 5 Brands';
            font-weight: 400;
            font-size: 20px;
            color:red;
            margin-right: 10px;
        }
    </style>
</head>
<body>
    <ul>
        <li>第一个li标签</li>
        <li>第二个li标签</li>
        <li>第三个li标签</li>
        <li>第四个li标签</li>
    </ul>
</body>
```
#### 6.3.2 通过实体来设置图标字体
通过实体来使用图标字体：`&#x图标编码;`
```
<head>
    <meta charset="UTF-8">
    <title>通过实体来添加图标</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<body>
    <span class="fa">&#xf270;</span>
</body>
```
### 6.4 行高：line height
行高指的是文字占有的实际高度，可以通过`line height`来设置行高 <br/>
- 行高可以直接指定一个大小(`px`,`em`)，也可以直接为行高设置一个整数
  - 如果是一个整数，行高将会是字体指定的倍数。默认行高为1.33。<br/>
  `margin-top：-200px;`
``` 
div{
    width: 900px;
    font-size: 40px;
    border: 1px red solid;
    /* 行高为80px */
    line-height: 2;
    }
<div>今天天气真不错，Hello Hello</div>
```
- 可以将行高设置为和高度一样的值，使单行文字在一个元素中垂直居中
```
div{
    font-size: 50px;
    height: 200px; //可省略
    line-height: 200px;
}
```
- 行高经常用来设置文字的行间距 <br/>
行间距 = 行高 - 字体大小 <br/>
```
/* 行间距是150px */
div{
    font-size: 50px;
    height: 200px; //可省略
    line-height: 200px;
}
```
### 6.5 字体框
字体框就是字体存在的格子，设置`font-size`实际上就是在设置字体框的高度。<br/>
行高会在字体框的上下平均分配。<br/>
### 6.6 字体的简写属性
 - `font` 可以设置字体相关的所有属性 <br/>
 语法 <br/>
 `font`：字体大小/行高 字体族 （行高可省略）<br/>
 ```
 /* 行高可省略 */
`font: 50px/2 'Times New Roman',Times,serif;`
```
- `font-weight` 字重，字体的加粗 <br/>
可选值：<br/>
  - `normal`：默认值 不加粗  
  - `bold`：加粗  `font-weight: bold;`
  - `100-900`：九个级别 `font-weight: 100;` //不常用
- `font-style`：字体的风格
  - `normal`：正常的
  - `italic`：斜体
`font: bold italic 50px/2 'Times New Roman',Times,serif;`
### 6.7 文本的水平和垂直对齐
- `text-align`：文本的水平对齐 <br/>
可选值：<br/>
  - `left`：左对齐
  - `right`：右对齐
  - `center`：居中对齐
  - `justify`：两端对齐
- `vertical-align`：设置元素垂直对齐的方式
可选值：<br/>
  - `baseline`：默认值，基线对齐
  - `top`：顶部对齐
  - `bottom`：底部对齐
  - `middle`：居中对齐
  - 直接指定值：`vertical-align:100px;`
  - 图片对齐：`vertical-align:top/bottom`
### 6.8 其他的文本样式
- `text-decoration`：设置文本修饰 <br/>
可选值：<br/>
  - `none`：什么都没有
  - `underline`：下划线
  - `line-through`：删除线
  - `overline`：上划线
```
  /* 红色点状下划线 */
  text-decoration: underline red dotted;
```
- `white-space`：设置网页如何处理空白 <br/>
 可选值：<br/>
   - `normal`：正常
   - `nowrap`：不换行
   - `pre`：保留空白 <br/>
例子：京东新闻栏题目溢出的部分用省略号显示
```
.box2{
    width: 200px;
    /* 不换行 */
    white-space: nowrap;
    /* 隐藏溢出部分 */
    overflow: hidden;
    /* 溢出的部分改为省略号 */
    text-overflow: ellipsis;
 }
 ```
## 7. 背景
### 7.1 常用属性
 - `background-color`：背景色
 - `background-image`：背景图片
  - 可以同时设置背景图片和背景颜色，这样背景颜色将会成为图片的背景色
  - 如果背景图片小于元素，则背景图片会自动在元素中平铺将元素铺满
  - 如果背景图片大于元素，将会有一部分背景无法完全显示
  - 如果背景图片和元素一样大，则会直接正常显示
  - 例子：`background-image:url("./img/i.png")`
- `background-repeat`：用来设置背景的重复方式
可选值：<br/>
  - `repeat`：默认值，背景会沿着x轴和y轴双方向重复
  - `repeat-x`：沿着x轴方向重复
  - `repeat-y`：沿着y轴方向重复
  - `no-repeat`：背景图片不重复
- `background-position`：用来设置图片的位置
设置方式：<br/>
  - 通过`top`，`left`，`right`，`bottom`，`center`几个表示方位的词来设置背景图片的位置
  - 例子：`background-position: top left;``background-position: center center;`
  - 使用方位词时必须要同时指定两个值，如果只写一个则第二个默认就是`center`
  - 通过偏移量来指定背景图片的位置：水平方向的偏移量，垂直方向的偏移量
  - 例子：`background-position: -50px 100px;`
- `background-clip`：设置背景的范围
可选值：<br/>
  - `border-box`：默认值，背景出现在边框的下边
  - `padding-box`：背景不会出现在边框里，只出现在内容区和内边距
  - `content-box`：背景只会出现在内容区
- `background-origin`：背景图片的偏移量计算的原点
可选值：<br/>
  - `padding-box`：默认值，`background-position`从内边距处开始计算
  - `content-box`：背景图片的偏移量从内容区处计算
  - `border-box`：背景图片的变量从边框处开始计算
- `background-size`：设置背景图片的大小 
  - 第一个值表示宽度，第二个值表示高度（如果只写一个，则第二个值默认是`auto`）
  - `cover`：图片的比例不变，将元素铺满
  - `contain`：图片比例不变，将图片在元素中完整显示
- `background-attachment`：背景图片是否跟随元素移动
可选值：<br/>
  - `scroll`：默认值，背景图片会跟随元素移动
  - `fixed`：背景图片会固定在页面中，不会随元素移动
- `background`：背景相关的简写属性，所有背景相关的样式都可以通过该样式来设置，并且该样式没有顺序要求，也没有哪个属性是必须写的
注意点：<br/>
  - `background-size`必须写在`background-position`之后，并且用`/`隔开：`background-position/background-size`
  - 例子：`background：url('./img/1.jpg') #bfa center center/contain no-repeat`
  - `background-origin` `background-clip`两个样式，`origin`要在`clip`的前边
- 渐变图：渐变导航条
  - 设置渐变导航条的宽度和高度
  - 将背景图片截1px宽，将其导入
  - 设置x轴背景图片重复
```
<head>
    <meta charset="UTF-8">
    <title>渐变图</title>
    <style>
        .box1{
            width: 800px;
            height: 23px;
            margin: 0 auto;
            background-image: url("pic/07/1.png");
            background-repeat: repeat-x;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
</body>
```
- 雪碧图：解决图片闪烁的问题
可以将多个小图片统一保存到一个大图片中，然后通过调整`background-position`来显示相应的图片 <br/>
这样图片会同时加载到网页中，就可以有效的避免出现闪烁的问题。<br/>
这个技术在网页中应用十分广泛，被称为`CSS-Sprite`，这种图被称为雪碧图。<br/>
  - 雪碧图的使用步骤：<br/>
    - 先确定要使用的图标
    - 测量图标的大小
    - 根据测量结果创建一个元素
    - 将雪碧图设置为元素的背景图片
    - 设置一个偏移量以显示正确的图片
```
.box1{
    width:42px;
    height:30px;
    background-image:url("./img/09/amazon-sprite.png");
    background-position:-58px -338px;
}
```
  - 雪碧图的特点：一次性将多个图片加载进页面，降低请求的次数，加快访问速度，提升用户的体验
### 7.2 渐变
通过渐变可以设置一些复杂的背景颜色，可以实现从一个颜色向其他颜色过渡的效果<br/>
渐变是图片，需要通过`background-image`来设置。
### 7.2.1 线性渐变
- `linear-gradient()`：颜色沿着一条直线发生变化 <br/>
  `linear-gradient(red,yellow);`：红色在开头，黄色在结尾，中间是过渡区域 <br/>
  - 线性渐变的开头，我们可以指定一个渐变的方向
    - `to left`：向左
    - `to right`：向右
    - `to bottom`：向下
    - `to top`：向上
    - `xxx deg`：表示旋转度数
    - `xxx turn`：表示圈
```  
/* 从右向左，从红色到黄色渐变 */
background-image: linear-gradient(to left,red,yellow);
```
  - 渐变可以同时指定多个颜色，多个颜色默认情况下平均分布，也可以手动指定渐变的分布情况 <br/>
  `background-image: linear-gradient(red 50px,yellow 100px,grenn 120px);`
- `repeating-linear-gradient();`：可以平铺的线性渐变 <br/>
`background-image: repeating-linear-gradient(red 50px,yellow 100px);`
### 7.2.2 径向渐变
- `radial-gradient()`：径向渐变，放射性效果，从中心往四周发射 <br/>
`background-image:radial-gradient(red,yellow);` <br/>
默认情况下径向渐变圆心的形状根据元素的形状来计算的，可以手动指定径向渐变的大小 <br/>
  - 正方形 --> 圆形
  - 长方形 --> 椭圆形 <br/> 
`background-image:radial-gradient(100px 100px,red,yellow);`
  - `circle`：正圆
  - `ellipse`：椭圆 <br/>
`background-image:radial-gradient(ellipse,red,yellow);`
  - 可以指定渐变的位置：`background-image:radial-gradient(100px 100px at 100px 100px,red,yellow);` <br/>
  语法：`radial-gradient(大小 at 位置, 颜色 位置, 颜色 位置);` <br/> 
  大小：<br/>
    - `circle`：圆形
    - `ellipse`：椭圆
    - `closest-side`：近边
    - `closest-corner`：近角
    - `farthest-side`：圆边
    - `farthest-corner`：远角
  位置：<br/>
    - `top`
    - `right`
    - `left`
    - `center`
    - `bottom`
## 8. 过渡
通过过渡可以指定一个属性发生变化时的切换方式 <br/>
通过过渡可以创建一些非常好的效果，提升用户的体验 <br/>
- 属性 <br/>
  - `transition-property`：指定要执行过渡的属性。
    - 多个属性用`,`隔开
    - 如果所有属性都需要过渡，则使用`all`关键字
    - 大部分可计算的属性都支持过渡效果
    - 注意：过渡时必须时从一个有效数值向另外一个有效数值进行过渡
    - 例子：`transition-property: width,height;` `transition-property: all;`
  - `transition-duration`：指定过渡效果的持续时间
    - 时间单位：`s`和`ms`
    - 例子：`transition-duration: 2s;`
  - `transition-timing-function`：过渡的时序函数，指定过渡的执行的方式
    可选值：<br/>
    - `ease`：默认值，慢速开始，先加速，后减速
    - `linear`：匀速运动
    - `ease-in`：加速运动
    - `ease-out`：减速运动
    - `ease-in-out`：先加速，后减速
    - `cubic-bezier()`：指定时序函数：<https://cubic-bezier.com>
    - `steps()`：分步执行过渡效果
    可以设置一个第二个值 <br/>
      - `end`：在时间结束时执行过渡（默认值）
      - `start`：在时间开始时执行过渡 
  - `transition-delay`：过渡效果的延迟，等待一段时间后再执行过渡 
  - `transition`：可以同时设置过渡相关的所有属性，只有一个要求：如果要写延迟，则两个时间中第一个是持续时间，第二个是延迟
## 9. 动画
动画和过渡类似，都是可以实现一些动态的效果，不同的是过渡需要在某个属性发生变化时才会触发，而动画可以自动触发动态效果 <br/>
设置动画效果，必须先要设置一个关键帧，关键帧设置了动画执行每一个步骤。 <br/>
```
@keyframes test{
  /* from表示动画的开始位置，也可以使用0% */   
  from{ 
    margin-left: 0;
  }
  /* to表示动画的结束位置 */
  to{
    margin-left: 700px;
  }
}
.box1{
  background-color: #bfa;

  /* animation-name：要对当前元素生效的关键帧的名字 */
  animation-name: test;

  /* animation-name：动画的执行时间 */
  animation-duration: 4s;

  /* animation-delay：动画的延时 */
  animation-delay: 2s;

  /* animation-timing-function：运动的方式（以下为匀速运动，其他运动参考过渡笔记） */
  animation-timing-function: linear;

  /* animation-iteration-count：动画执行的次数 
    可选值：
      - 次数
      - infinite：无限执行
  */
  animation-iteration-count: 3;

  /* animation-direction 指定动画运行的方向 
    可选值：
      - normal：默认值 从from向to运行 每次都是这样
      - reverse：从to向from运行 每次都是这样
      - alternate：从from向to运行 重复执行动画时反向执行
      - alternate-reverse：从to向from运行 重复执行动画时反向执行
  */
  animation-direction: alternate-reverse;

  /* animation-play-state：设置动画的执行状态
    可选值：
      - running：默认值 动画执行
      - paused：动画暂停  
   */
  animation-play-state: paused;

  /* animation-fill-mode：动画的填充模式 
    可选值：
      - none：默认值 动画执行完毕，元素回到原来位置
      - forwards：动画执行完毕，元素停止在动画结束的位置
      - backwards：动画延时等待时，元素就会处于开始位置
      - both：结合了forwards和backwards
   */
  animation-fill-mode: none;

  /* 综合 */
  animation: test 2s 2 1s;

}

```


