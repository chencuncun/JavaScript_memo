# Web开发笔记
## HTML
### 1. 基础标签
- `<head>`：头
- `<body>`：身体
- `<h1>`~`<h6>`：标题
- `<p>`：段落
- `<br/>`：改行
### 2. 属性
- `class`：规定元素的类名
- `id`：规定元素唯一ID
- `bgcolor`：背景色 <br>
`<body bgcolor="#8b0000"></body>`
- `align`: 位置 <br>
`<h1 align="right">标题1</h1>`
- `target`：网页打开方式
```
<a href="www.google.co.jp" target="_blank">另开网页</a>
<a href="www.google.co.jo" target="_self">本网页</a>
```
- `href`：指向另一个文档的链接
- `name`：创建文档内的链接 
### 3. 格式标签
- `<b>`：粗体文本  
- `<big>`：大号字
- `<small>`：小号字
- `<em>`：语气加重
- `<i>`：斜体字
- `<strong>`：表示强调，重要内容
- `<sub>`：上标字
- `<sup>`：下标字
- `<ins>`：插入字
- `<del>`：删除字
- `<hr>`：水平线(自闭标签)
- `<blockquote>`: 引用(块元素/自动换行)
- `<q>`: 短引用(行内元素/不换行)
### 4. 样式
#### 4.1 标签
- `<style>`: 样式定义
- `<link>`: 资源定义
#### 4.2 属性
- `rel="stylesheet"`：外部样式表
- `type="text/css"`：引入文档的类型
- `margin-left`：边距（居左，居中，居右）
#### 4.3 方法
##### 4.3.1 外部样式表
`<link rel="stylesheet" type="text/css" href="mystyle.css">`
##### 4.3.2 内部样式表
```
<style type="text/css">
body{
    background-color:red
}
p{
    margin-left:20px
}
</style>
```
##### 4.3.3 内联样式表
`<p style="color:red">`
### 5. 链接
#### 5.1 链接数据
- 文本链接 <br>
`<a href="http://www.google.co.jp">点击我</a>`
- 图片链接 <br>
`<a href="http://www.google.co.jp"><img src="pic/yaoyao.jpeg"></a>`
#### 5.2 属性
- href属性：指向另一个文档的链接
`<a href="#tips">跳转到hello</a>`
- name属性：创建文档内的链接
`<a name="tips">hello</a>`
#### 5.3 img标签属性
- `alt`：替换文本属性:当图片显示不出来的时候，可以显示该图片的内容注释
- `width`：宽
- `height`：高 <br>
`<a href="http://www.google.co.jp"><img src="pic/yaoyao.jpeg" width="100px" height="80px" alt="yaoyao"></a>`
### 6.表格
#### 6.1 标签
- `<table>`：定义表格
- `<caption>`：定义表格标题
- `<th>`：定义表格的表头
- `<tr>`：定义表格的行
- `<td>`：定义表格的单元
- `<thead>`：定义表格的页眉
- `<tbody>`：定义表格的主体
- `<tfoot>`：定义表格的页脚
- `<col>`：定义表格的列属性
#### 6.2 标签属性
- `cellpadding`：单元格边距
- `cellspacing`：单元格间距
- `bgcolor`:表格内的背景颜色
- `background`：表格内的背景图像
#### 6.3 表格例子
```
<table border="8" background="../pic/yaoyao.jpeg">
<caption>表格一</caption>
<tr>
    <th>1</th>
    <th>2</th>
    <th>3</th>
</tr>
<tr>
    <td>单元格1</td> 
    <td>单元格2</td>
    <td>单元格3</td>
</tr>
<tr>
    <td>单元格1</td>
    <td>单元格2</td>
    <td>单元格3</td>
</tr>
</table>
```
### 7.列表
#### 7.1 标签
- `ol`：有序列表
- `ul`：无序列表
- `li`：列表项
- `dl`：列表
- `dt`：列表项
- `dd`：描述 
#### 7.2 无序列表
- 标签：`<ul>`，`<li>`
- 属性：`disc`，`circle`，`square`
#### 7.3 有序列表
- 标签：`<ol>`，`<li>`
- 属性：`A`，`a`，`I`，`i`，`start`
#### 7.4 嵌套列表
- 标签：`<ul>`，`<ol>`，`<li>`
#### 7.5 自定义列表
- 标签：`<dl>`，`<dt>`，`<dd>`
#### 7.6 例子
```
<!--无序列表嵌套-->
<ul>
    <li>动物</li>
    <ul>
        <li>狗</li>
        <li>猫</li>
        <li>兔</li>
    </ul>
    <li>水果</li>
    <ul>
        <li>苹果</li>
        <li>橘子</li>
        <li>香蕉</li>
    </ul>
        <li>蔬菜</li>
    <ul>
        <li>菠菜</li>
        <li>青椒</li>
        <li>白菜</li>
    </ul>
</ul>
```
### 8. 块
#### 8.1 HTML块元素
块元素在显示时，通常会以新行开始 <br>
如：`<h1>`,`<p>`,`<ul>`
#### 8.2 HTML内联元素
内联元素通常不会以新行开始 <br>
如：`<b>`,`<a>`,`<img>`
#### 8.3 HTML`<div>`元素
`<div>`元素也被成为块元素，其主要时组合HTML元素的容器
#### 8.4 HTML`<span>`元素
`<span>`元素是内联元素，可作为文本的容器
### 9. 布局
#### 9.1 使用`<div>`元素布局
#### 9.2 使用`<table>`元素布局
### 10. 表单
#### 10.1 用于获取不同类型的用户输入
#### 10.2 常用表单标签
- `<form>`：表单
- `<input>`：输入域
- `<textarea>`：文本域
- `<label>`：控制标签
- `<fieldset>`：定义域
- `<legend>`：域的标题
- `<select>`：选择列表
- `<optgroup>`：选项组
- `<option>`：下拉列表中的选项
- `<button>`：按钮
#### 10.3常用属性
##### 10.3.1 用户/密码
```
用户名：
<input type="text">
密码：
<input type="password">
```
#### 10.3.2 复选框
```
苹果<input type="checkbox">
香蕉<input type="checkbox">
橘子<input type="checkbox">
```
每一个复选框都应该嵌套在它自己的`label`（标签）元素中。
所有关联的复选框应该拥有相同的`name`属性。
最佳实践是在`label`元素上设置`for`属性，让其值与复选框的`id`属性值相等，
这样就在`label`元素和它的子元素复选框之间创建了一种链接关系。
```
<form>
    <label for="loyalty"><input id="loyalty" type="checkbox" name="personality">忠诚</label>
    <label for="enterprising"><input id="enterprising" type="checkbox" name="personality">进取</label>
    <label for="introvert"><input id="introvert" type="checkbox" name="personality">内向</label>
</form>
```
#### 10.3.3 单选按钮
```
性别:
男<input type="radio" name="sex">
女<input type="radio" name="sex">
```
每一个单选按钮都应该嵌套在它自己的`label`（标签）元素中。<br>
最佳实践是在`label`元素上设置`for`属性，让其值与单选按钮的`id`属性值相等，
这样就在`label`元素和它的子元素单选按钮之间创建了一种链接关系。
```
<form>
    <label for="indoor">
        <input id="indoor" type="radio" name="indoor-outdoor">indoor
    </label>
    <label for="outdoor">
        <input id="outdoor" type="radio" name="indoor-outdoor">outdoor
    </label>
</form>
```
##### 10.3.4 下拉列表
```
请选择您喜欢的水果：
<select>
    <option>---苹果---</option>
    <option>---橘子---</option>
    <option>---香蕉---</option>
</select>
```
##### 10.3.5 文本域
`<textarea cols="30" rows="30">请填写个人信息</textarea>`
##### 10.3.6 按钮
```
<input type="button" value="按钮">
<input type="submit" value="确认">
```
#### 10.3.7 默认选中
通过添加`checked`属性，可以设置某个单选按钮或多选按钮被默认选中 <br/>
为此只需要给`input`元素添加`checked`属性。
```
<input type="radio" name="test-name" checked>
```
### 11. 框架
#### 11.1 常用标签
- `<noresize>`: 固定框架大小
- `<cols>`: 列
- `<rows>`: 行
#### 11.2 内联框架
- `<iframe>`
```
<!--Frame.html-->
<body>
    <iframe src="Frame_c.html" frameborder="0" width="800px" height="800px"></iframe>
</body>
```
```
<!--Frame_a.html-->
<body bgcolor="#6495ed">
    frame_a
    <br/>
    <a href="https://www.baidu.com/" target="_parent">百度主页</a>
</body>
```
```
<!--Frame_b.html-->
<body bgcolor="#008b8b">
    frame_b
    <iframe src="Frame_a.html" width="400px" height="400px"></iframe>
</body>
```
```
<!--Frame_c.html-->
<body bgcolor="#a52a2a">
    frame_c
    <iframe src="Frame_b.html" width="600px" height="600px"></iframe>
</body>
```
### 12. 背景
#### 12.1 标签
- `<background>`:背景图片
- `<bgcolor>`:背景颜色
#### 12.2 颜色
- 由一个十六进制符号来定义，这个符号由红色，绿色和蓝色的值组成。
- 颜色值最小值：0（`#00`）
- 颜色值最大值：255（`#FF`）
- 红色：`#FF0000`
- 绿色：`#00FF00`
- 蓝色：`#0000FF`
### 13. XHTML
#### 13.1 简介
- XHTML指的是可扩展超文本标记语言
- XHTML与HTML4.01几乎是相同的
- XHTML是更严格更纯净的HTML版本
- XHTML是以XML应用的方式定义的HTML
- XHTML得到所以主流浏览器的支持
#### 13.2 优点
为了代码的完整性和良好性
#### 13.3 文档声明
- DTD：规定了使用通用标记语言的网页语法
#### 13.4 三种XHTML文档类型
- STRICT(严格类型)
- TRANSITIONAL(过渡类型)
- FRAMESET(框架类型)
#### 13.5 元素语法
- XHTML元素必须正确嵌套
- XHTML元素必须始终关闭
- XHTML元素必须小写
- XHTML文档必须有一个根元素
#### 13.6 属性语法
- XHTML属性必须使用小写
- XHTML属性值必须用引号包围
- XHTML属性最小化也是禁止的
### 14. 全局属性
- `contentEditable`：可编辑列表 <br>
```
<ul contenteditable="false">
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
</ul>
```
- `designMode`：整个页面是否可编辑，只能在Javascript脚本里被修改编辑 <br>
  - `on`：可编辑 <br>
  - `off`：不可编辑 <br>
- `hidden`：通知浏览器不渲染该元素 <br>
  - `true`：元素处于不可见状态 <br>
  - `false`：元素处于可见状态 <br>
```
<h3>不可见列表</h3>
<ul hidden="">
    <li>列表1</li>
    <li>列表2</li>
    <li>列表3</li>
</ul>
```
- `spellcheck`: 针对`input`和`textarea`元素提供的属性,对输入文本进行拼写检查 <br>
```
<!--spellcheck-->
<input type="text" spellcheck="true">
```
- `tabindex`:tab键的位置
```
<!--tabindex-->
<a href="#" tabindex="1">hello</a>
<a href="#" tabindex="3">hello</a>
<a href="#" tabindex="2">hello</a>
```
### 15.主体结构元素
- `<article>` <br>
可以嵌套使用，也可用来表示插件 <br>
```
<article>
    <header>
        <h1>header</h1>
        <p>hello,header</p>
    </header>
    <article>
        <header>作者</header>
        <p>评论</p>
        <footer>时间</footer>
    </article>
    <foorer>
        <p>This is footer</p>
    </foorer>
</article>
```
`<embed src="#" width="600" height="400">`:将外部内容嵌入文档中的指定位置 <br>
- `<section>` <br>
用于对网站或应用程序中页面上的内容进行分块，通常由内容和标题组成。<br>
`section`元素并非一个普通的容器元素；当一个容器需要被直接定义样式或通过脚本定义行为时，推荐使用`div`而非`section`元素。<br>
- `<nav>` <br>
是一个可以用作页面导航的连接组，其中的导航元素链接到其他页面或当前页面的其他部分。<br>
并不是所有的连接组都要被放进`nav`元素，只需要将主要的，基本的连接组放进`nav`元素即可。<br>
`nav`元素应用场景：<br>
  - 传统导航条
  - 侧边栏导航
  - 页内导航
  - 翻页操作 <br>
```
<nav>
    <ul>
        <li><a href="#HTML">HTML的历史</a></li>
        <li><a href="#CSS">CSS的历史</a></li>
    </ul>
</nav>
```
- `<aside>` <br>
用来表示当前页面或文章的附属信息部分，它可以包含与当前页面或主要内容相关的引用，侧边栏，广告，导航条，<br>
以及其他类似的有区别与主要内容的部分。<br>
```
<header>
    <h1>js入门</h1>
</header>
<article>
    <h1>语法</h1>
    <p>文章的正文</p>
    <aside>
        <h1>名词的解释</h1>
        <p>语法：这是一个对语言来说很重要的内容体</p>
    </aside>
</article>
<aside>
    <nav>
        <h2>评论</h2>
        <ul>
            <li><a href="#">2018-10-10</a></li>
            <il><a href="#">内容不错！</a></il>
        </ul>
    </nav>
</aside>
```
- `<time>`与微格式: <br>
```
<time datetime="2020-9-8">2020-9-8</time>
<time datetime="2020-9-8T20:00">2020-9-8</time>
<time datetime="2020-9-8T20:00Z">2020-9-8</time>
<time datetime="2020-9-8T20:00+09:00">2020-9-8</time>
``` 
- `pubdate`属性 <br>
```
<article>
    <header>
        <h1>苹果</h1>
        <p>发布日期
            <time datetime="2020-9-8" pubdate>2020-9-8</time>
        </p>
        <p>发货日期
            <time datetime="2020-9-9">2020-9-9</time>
        </p>
    </header>
</article>
```
### 16.非主体结构元素
- `<header>` <br>
一种具有引导和导航作用的结构元素，用来防止整个页面或页面内的一个内容区块的标题，<br>
但也可以包含其他内容，例如数据表格，搜索表单或相关的logo图片 <br>
```
<header>
    <h1>IT</h1>
    <a href="http://google.co.jp">google</a>
    <nav>
        <ul>
            <li><a href="#">1</a></li>
            <li><a href="#">2</a></li>
            <li><a href="#">3</a></li>
        </ul>
    </nav>
</header>
```
- `<footer>` <br>
可以作为其上层父级内容区块或是一个根区块的脚注。<br>
`footer`通常包括其相关区块的脚注信息，如作者，相关阅读链接及版权信息等。<br>
```
<footer>
    <ul>
        <li>作者</li>
        <li>版权</li>
    </ul>
</footer>
```
- `<hgroup>` <br>
将标题及其子标题进行分组的元素。`hgroup`元素通常会将`h1`~`h6`元素进行分组，譬如一个内容区块的标题及其子元素算一组。<br>
``` 
<header>
    <hgroup>
        <h1>h1</h1>
        <h2>h2</h2>
    </hgroup>
</header>
```
- `<address>` <br>
用来在文档中呈现联系信息，包括文档作者或文档维护者的名字，他们的网站链接，电子邮件，真实地址，电话号码等。<br>
`address`应该不只用来呈现电子油箱或真实地址，还用来展示跟文档相关的联系人的所有联系信息。<br>
```
<footer>
    <div>
        <address>
            <a href="#">联系方式</a>
            <time datetime="2020-9-9">2020-9-9</time>
        </address>
    </div>
</footer>
```
### 17.表单属性
- `<form>` <br>
- `formaction` <br>
单击不同的按钮时可以将表单提交到不同的页面 <br>
```
<form id="testform">
    <input type="submit" name="s1" value="v1" formaction="xx1.jsp">第一页
    <input type="submit" name="s2" value="v2" formaction="xx2.jsp">第二页
    <input type="submit" name="s3" value="v3" formaction="xx3.jsp">第三页
</form>
```
- `formmethod` <br>
对每一个表单元素分别指定不同的提交方法 <br>
```
<form id="testform">
    <input type="submit" name="s1" value="v1" formmethod="post" formaction="xx01.jsp">
    <input type="submit" name="s2" value="v2" formmethod="get" formaction="xx02.jsp">
</form>
```
- ?`formenctype` <br>
用于指定在表单发送到服务其之前应该如何对表单内的数据进行编码,html5中的`formenctype`属性对表单分别指定不同的编码方式 <br>
```
<form>
    <input type="text" formenctype="text/plain">
    <input type="text" formenctype="multipart/form-data">
    <input type="text" formenctype="application/x-www-form-urlencoded">
</form>
```
- `formtarget` <br>
用于指定在何处打开表单提交后所需要加载的页面 <br>
```
<form>
    <input type="submit" name="s1" value="v1" formtarget="_blank" formaction="xx1.jsp">第一页
    <input type="submit" name="s2" value="v2" formtarget="_self" formaction="xx2.jsp">第二页
    <input type="submit" name="s3" value="v3" formtarget="_parent" formaction="xx3.jsp">第三页
    <input type="submit" name="s4" value="v4" formtarget="_top" formaction="xx4.jsp">第四页
    <input type="submit" name="s4" value="v4" formtarget="framename" formaction="xx5.jsp">第五页
</form>
```
- `autofocus` <br>
为文本框，选择框或按钮控件加上`autofocus`属性，当画面打开时，该控件自动获取光标焦点 <br>
```
<form>
    <input type="text" autofocus>
    <input type="text">
</form>
```
- `required` <br>
可以应用在大多数输入元素上。在提交时，如果元素中内容为空白，则不允许提交，同时在浏览器中显示信息提示文字<br>
```
<form action="xx01.jsp">
    <input type="text" required="required">
    <button type="submit">提交</button>
</form>
```
- ？`labels` <br>
为所有可使用标签的表单元素，`button`，`select`元素等，定义一个`labels`属性 <br>
属性值为一个`NodeList`对象，代表该元素所绑定的标签元素所构成的集合。<br>
- ？`control` <br>
可以在标签内部放置一个表单元素，并且通过该标签的`control`属性来访问该表单元素 <br>
- `placeholder` <br>
是指当文本框处于未输入状态时显示的输入提示。当文本框处于未输入状态且未获取光标焦点时，模糊显示输入提示文字。<br>
`<input type="text" placeholder="请输入用户名 ">`
- `list` <br>
类似于选择框，但当用户想要设定的值不在选择列表之内时，允许自行输入。<br>
```
<form>
    <input type="text" name="greeting" list="greetings">
    <datalist id="greetings" style="display: none">
        <option value="HTML5">HTML5</option>
        <option value="CSS">CSS</option>
        <option value="Javascript">Javascript</option>
    </datalist>
</form>
```
- ?`AutoComplete` <br>
规定输入字段是否应该启用自动完成功能<br>
```
<form>
    <input type="text" name="greeting" autocomplete="on" list="greetings">
    <datalist id="greetings" style="display: none">
    <option value="HTML5">HTML5</option>
    <option value="CSS">CSS</option>
    <option value="Javascript">Javascript</option>
    </datalist>
</form>
```
- `pattern` <br>
对input元素使用pattern属性，并且将属性值设为某个格式的正则表达式，在提交时会针对这些进行检查，检查其内容是否合格给定格式。<br>
当输入内容不符合给定格式时，则不允许提交，同时在浏览器中显示提示文字,提示输入的内容必须符合给定格式。 <br>
```
<form>
    请输入内容：
    <input pattern="[A-Z]{3}" name="part">
    <input type="submit">
</form>
```
- ?`SelectionDirection` <br>
对`input`和`textarea`元素，增加了该属性。 <br>
当用户在这两个元素中用鼠标选取部分文字时，可以使用该属性来获取方向。<br>
当用户正在选取文字时，该属性值为"`forward`"，<br>
当用户反向选取文字时，该属性值为"`backward`"。<br>
当用户没有选取任何文字时，该属性值为"`forward`"。<br>
- ?`indete` `rminate` <br>
对复选框`checkbox`元素来说过去只是选取与非选取这两种状态。<br>
在HTML5中，可以在JavaScript脚本代码中对该元素使用该属性，以说明复选框出去"尚未明确是否选取"状态。<br>
- `image` <br>
提交按钮的`height`属性和`width`属性，针对类型为`image`的`input`元素，HTML5新增了两个属性，`height`，`width`分别用来指定图片按钮的高度和宽度 <br>
```
<form action="test.jsp" method="post">
    姓名：<input type="text" name="name">
    <input type="image" src="xx.jpeg" alt="这是一张风景图片" width="60" height="40">
</form>
```
### 18.标签
#### 18.1 块元素
在页面中独占一行的元素 <br/>
如：`<h1>`~`<h6>`，`<p>`
#### 18.2 行内元素或内联元素
在页面中不会独占一行的元素 <br/>
如：`<em>`
#### 18.3 注意
块元素可以包含块元素和行内元素，但是行内元素不能包含块元素。<br/>
特例：`<p>`标签不可以包含块元素。
### 19. html结构
`<header>`：头部(一个页面可以有多个) <br/>
`<main>`：主体(一个页面中只有一个) <br/>
`<footer>`：底部(一个页面可以有多个) <br/>
`<nav>`：导航 <br/>
`<aside>`：侧边栏 <br/>
`<article>`：表示一个独立文章(含有标题) <br/>
`<section>`：表示一个独立的区块 <br/>

`<div>`：是一个块元素，没有语义，是目前主要的布局元素 <br/>
`<span>`：是一个行内元素，没有语义，一般用于在网页中选中文字 <br/>