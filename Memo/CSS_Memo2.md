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
- 补充：class是一个标签的属性，它和id类似，不同的是class可以重复使用。可以通过class属性来为元素分组，可以同时为一个元素指定多个class属性
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
    p[title^=abc]{
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
  - 内容区（content）
  - 内边距（padding）
  - 边框（border）
  - 外边距（margin）
### 3.2 盒子组成详解
#### 3.2.1 内容区（content）
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
#### 3.2.2 边框（border）
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
#### 3.2.3 内边距（padding）
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
#### 3.2.4 外边距（margin）
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

