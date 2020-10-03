#CSS 笔记重点

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

