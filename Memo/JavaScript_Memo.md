## JavaScript
### 0. 目录
### 1. 基础
### 5. 函数
### 1. 基础
#### 1.1 介绍
互联网上最流行的脚本语言，这门语言可用于Web和HTML，更可广泛用于服务器，pc端，移动端。
#### 1.2 脚本语言
是一种轻量级的编程语言。<br>
是可以插入HTML页面的编程代码。<br>
插入HTML页面后，可由所有的浏览器执行。
#### 1.3 用法
HTML中的脚本必须位于`<script></script>`标签之间。<br>
脚本可被放置在HTML页面的`<body>`和`<head>`部分中
#### 1.4 标签
在HTML中插入JavaScript，使用`<script>`标签<br>
在`<script></script>`之间书写代码

#### 1.5 使用权限
在HTML中，不限制脚本数量。通常会把脚本放置于`<head>`标签中，以不干扰页面内容

#### 1.6 输出
 JavaScript通常用来操作HTML <br>
- 文档输出
 ```
document.write("<p>JavaScript</p>");
 ```
- 更换内容: 将`pID`变更为`www.google.co.jp`
 ```
 <p id="pID">Hello</P>
 <script>
    document.getElementById("pID").innerHTML="www.google.co.jp";
 </script>
 ```
### 2. 语句
#### 2.1 定义
JavaScript语句向浏览器发出的命令。语句的作用是告诉浏览器该做什么。
#### 2.2 分号
语句之间的分割是分号（；）<br>
注意：分号是可选项，有时候看到不以分号隔开的。
#### 2.3 代码
按照编写顺序依次执行
#### 2.4 标识符
JavaScript标识符必须以字母，下划线或美元符号开始
JavaScript关键字
#### 2.5 大小写
JavaScript同样对大小写很敏感
#### 2.6 空格
忽略多余的空格
#### 2.7 注释
单行注释：// <br>
多行注释：/**/
### 3. 变量和数据类型
#### 3.1 变量
##### 3.1.1 变量是用来储存信息的"容器"
```
var x = 10；
var y = 10.2；
var z = "Hello"；
```
##### 3.1.2 局部变量和全局变量
- 局部变量：只能在当前函数中使用 <br>
- 全局变量：在任何地方都可以使用 <br>
```
<script>
    var n = 10; //全局变量
    m = 20; //全局变量
    function demo(){
        var i = 30; //局部变量
        j = 40; //全局变量
   }
   demo();
   alert(i);
 </script>
```
```
执行结果：无显示
```
#### 3.2 数据类型
##### 3.2.1 `String`：字符串
`var string = "Hello";`
##### 3.2.2 Number：数字
`var i1 = 10;`
##### 3.2.3 Boolean：布尔
`var flag = true;`
##### 3.2.4 `Array`：数组
```
var arr = ["apple","orange","banana"];
var arr2 = new Array("apple","orange","banana");
var arr3 = new Array();
    arr3[0] = "apple";
    arr3[1] = "orange";
    arr3[2] = "banana";
```
##### 3.2.5 `Object`：对象
##### 3.2.6 `null`：空 <br>
`var n = null;`
##### 3.2.7 未定义
`var r;`
##### 3.2.8 可以通过赋值为`null`的方式清除变量
```
var i1 = 10;
    i1 = null;
```
### 4. 语法
#### 4.1 运算符
##### 4.1.1 算数运算符
`+, -, *, %, /, ++, --` <br>
```
<p>i=10,j=10;i+j=?</p>
<p id="sumid"></p>
<button onclick="mySum()">result</button>
<script>
    function mySum() {
        var i = 10;
        var j = 10;
        var m = i + j;
    document.getElementById("sumid").innerHTML=m;
   }
</script>
```
##### 4.1.2 赋值运算符
`=, +=, -=, *=, /=, %=`
##### 4.1.3 字符串操作
```
<script>
    function mySum(){
        var i = "www.";
        var j = "google.co.jp";
        var m = i + j;
        document.getElementById("sumid").innerHTML=m;
    }
</script>
```
##### 4.1.4 比较运算符 
`==, ===（必须满足类型一样） !=, !==（必须满足类型一样），>, <, >=, <=`
##### 4.1.5 逻辑运算符
`&&，||， ！`
##### 4.1.6 条件运算符
例：<br>
`x<10?"x比10小"："x比10大"` 
#### 4.2 条件语句
##### 4.2.1 if~else
```
<script>
    var i = 6;
    if(i>=10){
        document.write("i>=10");
    }else{
        document.write("i<10");
   }
</script>
```
##### 4.2.2 switch
```
<script>
    var i=10;
    switch (i){
        case 1:
            document.write("i=1");
            break;
        case 2:
            document.write("i=2");
            break;
        case 10:
            document.write("i=10")；
            break;
        default:
            document.write("条件不满足case");
        break； 
   }
</script>
```
#### 4.3 循环语句
##### 4.3.1 for循环，for/in
```
<script>
    var i=[1,2,3,4,5,6];
    for(var j=0;j<6;j++) {
        document.write(i[j]+",");
    }
</script>
```
```
<script>
    var i=[1,2,3,4,5,6];
    var j;
    for(j in i){
        document.write(i[j]+"<br/>");
   }
</script>
```
##### 4.3.2 while循环，do～while
```
<script>
    var i = 1;
    while(i<10){
        document.write("i="+i+"<br/>");
        i++;
    }
</script>
```
```
<script>
    var i = 1;
    do{
        document.write("i="+i+"<br/>");
        i++;
    }while(i<10){
    }
</script>
```
#### 4.4 跳转语句
##### 4.4.1 break：跳出当前循环，不再进行下一次循环
```
<script>
    for(var i=0;i<10;i++){
        if(i==5){
            break;
        }
        document.write("i="+i+"<br/>");
    }
</script>
```
```
执行结果：
  i=0
  i=1
  i=2
  i=3
  i=4
```
##### 4.4.2 continue:结束本次循环，进入下一次循环
```
<script>
    for(var i=0;i<10;i++){
        if(i==5){
            continue;
        }
    document.write("i="+i+"<br/>");
  }
</script>
```
```
执行结果：
  i=0
  i=1
  i=2
  i=3
  i=4
  i=6
  i=7
  i=8
  i=9
```
### 5. 函数
#### 5.1 概要
函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。<br>
如：实现10组数字的和<br>
```
<script>
    function demo(a,b){
        var sum = a+b;
        return sum;
    }
    var v1 = demo(20,30);
    alert(v1);
</script>
```
#### 5.2 定义
##### 5.2.1 定义函数
```
function 函数名(){
    函数体；//代码块
}
```
##### 5.2.2 注意
JavaScript对大小写十分敏感，所以这里的`function`必须小写。在函数调用时，也必须按照函数的相同名称来调用函数。<br>
函数名头字母一般小写，如果出现两个单词，第二个单词首字母大写。<br>
#### 5.3 函数调用
##### 5.3.1 函数调用
函数在定义好之后，不能自动执行，需要进行调用
##### 5.3.2 调用方式
- 在`<script>`标签内调用 <br>
```
<script>
    function demo(){
        var a = 10;
        var b = 10;
        var sum = a+b;
        alert(sum);
   }
   demo();
</script>
```  
- 在HTML文件中调用 <br>
```
<script>
    function demo(){
        var a = 10;
        var b = 10;
        var sum = a+b;
        alert(sum);
   }
</script>
<button onclick="demo()">提交</button>
```
#### 5.4 带参数的函数
##### 5.4.1 函数参数
在函数的调用中，也可以传递值，这些值被称为参数 <br>
例：`demo(arg1,arg2)`<br>
```
<script>
    function demo(a,b){
        var sum = a+b;
        alert(sum);
   } 
   demo(10,10);
</script>
```
```
<script>
    function demo(name,age){
        alert("名字是："+name+"， 年龄是："+age);
    }
</script>
<button onclick="demo('Chen',30)">提交</button>
```
##### 5.4.2 注意
参数的个数可以为任意多，每个参数通过`"，"`隔开。参数在传递时，其顺序必须一致
##### 5.4.3 意义
通过传递参数的个数及参数的类型不同完成不同的功能 
#### 5.5 带返回值的函数
##### 5.5.1 返回值
有时需要将函数的值返回给调用它的地方 <br>
```
<script>
    function demo(){
        return "Hello";
   }
   var vl1 = demo()+":Chen"
   var vl2 = demo()+":Wang"
   alert(vl1);
   alert(vl2);
</script>
```  
```
<p id="pid"></p>
<script>
    function demo(a,b) {
        if(a>b){
            return "a大于b";
        }else if(a<b){
            return "a小于b";
        }else{
            return "a等于b";
        }
   }
   document.getElementById("pid").innerHTML=demo(20,30);
</script>
```
##### 5.5.2 注意
在使用`return`语句时，函数会停止执行，同时返回值
### 6. JavaScript异常捕获
#### 6.1 异常
当JavaScript引擎执行JavaScript代码时，发生了错误，导致程序停止运行
#### 6.2 异常抛出
当异常产生，并且将这个异常生成一个错误信息
#### 6.3 异常捕获
```
try{
    发生异常的代码块;
}catch(err){
    错误信息处理;
}
```
```
<script>
    function demo(){
        try{
            alert(str);
        }catch(err){
            alert(err);
        }
    }
    demo();
</script>
```
#### 6.4 Throw语句
通过`throw`语句创建一个自定义错误<br>
```
<form>
    用户名：
    <input id="txt" type="text">
    <br/>
    密码：
    <input id="password" type="password">
    <br/>
    <input id="button" type="button" onclick="demo()" value="提交">
</form>
<script>
    function demo(){
        try{
            var e = document.getElementById("txt").value;
            var f = document.getElementById("password").value;
            if(e==""){
                throw "请输入用户名";
            }if(f==""){
                throw "请输入密码";
            }
        }catch(err){
            alert(err);
        }
  }
</script>
```
### 7. JavaScript事件
#### 7.1 定义
事件是可以被JavaScript侦测到的行为
#### 7.2 主要事件
##### 7.2.1 `onClick`: 点击事件
```
<button onclick="demo()">提交</button>
<script>
    function demo() {
        alert("Hello");
    }
</script>
```
##### 7.2.2 `onMouseOver`: 鼠标经过事件 和 `onMouseOut`: 鼠标移出事件
```
<div class="div" onmouseover="onOver(this) onmouseout="onPut(this)""> </div>
<script>
    function onOver(ooj) { //鼠标经过事件
        ooj.innerHTML = "Hello";
    }
    function onPut(ooj) {  //鼠标移出事件
        ooj.innerHTML = "World";
    }
</script>
```
##### 7.2.3 `onChange`: 文本内容改变事件
```
<form>
    <input type= "text" onchange="changeDemo(this)">
</form>
<script>
    function changeDemo(){
        alert("文本内容改变了");
    }
</script>
```   
```
<form>
    <input type="text" onchange="alert('内容改变了')">
</form>
```
##### 7.2.4 `onSelect`: 文本框选中事件
```
<form>
    <input type="text" onselect="onSelectDemo(this)"> 
</form>
<script>
    function onSelectDemo(bg) {
        bg.style.backgroundColor="green";
    }
</script>
```
##### 7.2.5 `onFocus`: 光标聚集事件 和 `onBlur`: 光标移开事件
```
<form>
    <input type="text" onfocus="onFocusDemo(this)" onblur="onBlurDemo(this)"> 
</form>
<script>
    //光标聚集事件
    function onFocusDemo(bg) { 
        bg.style.backgroundColor="blue";
    }
    //光标移开事件
    function onBlurDemo(bg) {
        bg.style.backgroundColor="yellow";
    }
</script>
```
##### 7.2.6 `onLoad`: 网页加载事件 和 `onUnload`: 关闭网页事件
```
<body onload="msg()">
<script>
    function msg() {
        alert("网页加载成功");
    }
</script>
``` 
### 8. JavaScriptDOM对象
#### 8.1 DOM简介
 当网页被加载时，浏览器会创建页面的文档对象模型(Document Object Model)<br>
##### 8.1.1 DOM操作HTML
- JavaScript能改变页面中的所有HTML元素
- JavaScript能改变页面中的所有HTML属性
- JavaScript能改变页面中的所有CSS样式
- JavaScript能对页面中的所有事件作出反应
#### 8.2 DOM操作HTML
##### 8.2.1 改变HTML输出流
  注意：绝对不要在文档加载完成之后使用`document.write()`。这会覆盖该文档
##### 8.2.2 寻找元素
- 通过`id`找到HTML元素<br>
- 通过标签名找到HTML元素 <br>
```
<p id="pid">Hello</p>
<button onclick="demo()">提交</button>
<script>
    function demo() {
        document.getElementsByTagName("p");
    }
</script>
```
##### 8.2.3 改变HTML内容
`innerHTML` <br>

```
<p id="pid">Hello</p>
<button onclick="demo()">提交</button>
<script>
    function demo() {
        document.getElementById("pid").innerHTML="Hi";
    }
</script>
``` 
##### 8.2.4 改变HTML属性
`attribute` <br> 
```
<a id="aid" href="http://www.baidu.com">百度</a>
<button onclick="demo()">变换</button>
<script>
    function demo() {
        document.getElementById("aid").href="http://www.google.co.jp";
    }
</script>
```   
```
<img id="imgid" src="../../pic/cat.jpg">
<button onclick="demo()">转换</button>
<script>
    function demo() {
        document.getElementById("imgid").src="../../pic/dog.jpg";
    }
</script>
```
#### 8.3 DOM操作CSS
##### 8.3.1 通过DOM对象改变CSS
语法：<br>
`document.getElementById(id).style.property=new style` <br>

``` 
<!--html-->
<div id="div" class="div">Hello</div>
<button onclick="demo()">转换</button>
 
//CSS
.div{
    width: 100px;
    height: 100px;
    background-color: red;
    }
 
//javaScript
function  demo(){
    document.getElementById("div").style.backgroundColor="blue";
}
```
#### 8.4 DOM EventListener
##### 8.4.1 方法：`addEventListener()`:用于向指定元素添加事件句柄
```
<button id="buttonID">提交</button>
<script>
    document.getElementById("buttonID").addEventListener("click",function () {
        alert("hello");
    })
</script>
``` 
##### 8.4.2 方法：`removeEventListener()`：移除方法添加的事件句柄 <br>
```
<button id="buttonID">提交</button>
<script>
    var x = document.getElementById("buttonID");
        x.addEventListener("click",hello);
        x.addEventListener("click",world);
        x.removeEventListener("click",hello);
    function hello() {
        alert("Hello");
    }
    function world() {
        alert("World");
    }
</script>
```
### 9. 事件详解
#### 9.1 事件流
##### 9.1.1 事件流
描述的是在页面中接受事件的顺序
##### 9.1.2 事件冒泡
由最具体的元素接收，然后逐级向上传播至最不具体的元素的节点（文档）
##### 9.1.3 事件捕获
最不具体的节点先接收事件，而最具体的节点应该是最后接收事件
#### 9.2 事件处理
##### 9.2.1 HTML事件处理
直接添加到HTML结构中 <br>
```
<div id="divID">
    <button id="button1" onclick="demo()">提交</button>
</div>
<script>
    function demo() {
        alert("事件详细");
    }
</script>
```
##### 9.2.2 DOM0级事件处理
把一个函数赋值给一个事件处理程序属性 <br>
```
<div id="div">
    <button id="button1">提交</button>
</div>
<script>
    var button1 = document.getElementById("button1");
        button1.onclick = function () {
            alert("DOM0级事件处理程序1");//被覆盖掉
        }
        button1.onclick = function () {
            alert("DOM0级事件处理程序2");
        }
</script>
```
##### 9.2.3 DOM2级事件处理
- `addEventListener("事件名"，"事件处理函数"，"布尔值"）;`<br>
  - true:事件捕获 <br>
  - false:事件冒泡 <br>
- `removeEventListener();` <br>
```
<div id="divID">
    <button id="button1">提交</button>
</div>
<script>
    var btn1 = document.getElementById("button1");
        btn1.addEventListener("click",demo1);
        btn1.addEventListener("click",demo2);
        function demo1() {
            alert("DOM2级事件处理程序1");
        }
        function demo2() {
            alert("DOM2级事件处理程序2");
        }
        btn1.removeEventListener("click",demo2);//点击移除demo2
</script>
```
##### 9.2.4 IE事件处理程序
- `attachEvent`：添加一个事件 <br>
- `detachEvent`：移除一个事件 <br>
```  
<div id="divID">
    <button id="button1">提交</button>
</div>
<script>
    var btn1 = document.getElementById("button1");
    if(btn1.addEventListener){
        btn1.addEventListener("click",demo);
    }else if(btn1.attachEvent){
        btn1.attachEvent("onclick",demo);
    }else{
        btn1.onclick = demo();
    }
    function demo() {
        alert("Hello");
    }
</script>
```
#### 9.3 事件对象
##### 9.3.1 事件对象
在触发DOM事件的时候都会产生一个对象
##### 9.3.2 事件对象`event`
- `type`:获取事件类型 <br>
```
<div id="divID">
    <button id="button1">提交</button>
</div>
<script>
    document.getElementById("button1").addEventListener("click",showType);
    function showType(event) {
        alert(event.type);
    }
</script>
```
```
执行结果：click
```  
- `target`:获取事件目标 <br>
 ```
<div id="divID">
    <button id="button1">提交</button>
</div>
<script>
    document.getElementById("button1").addEventListener("click",showType);
    function showType(event) {
        alert(event.target);
    }
</script>
```
```
执行结果：
[object HTMLButtonElement]
```  
- `stopPropagation()`:阻止事件冒泡 <br>
```
<div id="divID">
    <button id="button1">提交</button>
</div>
<script>
    document.getElementById("button1").addEventListener("click",showTarget);
    document.getElementById("divID").addEventListener("click",showDiv);
    function showTarget(event) {
        alert(event.target);
    }
    function showDiv() {
        alert("div");
    }
</script>
```    
```
执行结果：
[object HTMLButtonElement] 
div
```   
以上代码出现事件冒泡现象，为了阻止此现象，将以上代码改成：
```
function showTarget(event) {
    alert(event.target);
    event.stopPropagation();//阻止事件冒泡
}
```
```
执行结果：[object HTMLButtonElement]
```  
- `preventDefault()`:阻止事件默认行为 <br>

```
<div id="divID">
    <button id="button1">提交</button>
    <a id="aID" href="http://www.google.co.jp">google</a>
</div>
<script>
    document.getElementById("button1").addEventListener("click",showTarget);
    document.getElementById("divID").addEventListener("click",showDiv);
    document.getElementById("aID").addEventListener("click",showA);
    function showTarget(event) {
        alert(event.target);
        event.stopPropagation();//阻止事件冒泡
    }
    function showDiv() {
        alert("div");
    }
    function showA(event){
        event.stopPropagation();//阻止事件冒泡
        event.preventDefault();//网页不会跳转
    }
</script>
```
### 10. 内置对象
#### 10.1 对象的解释
##### 10.1.1 JavaScript中的所有事物都是对象：字符串，数值，数组，函数...
每个对象带有属性和方法
##### 10.1.2 JavaScript允许自定义对象
- 定义并创建对象实例 <br>
```     
<script>
    //第一种定义方法
    people = new Object();
    people.name = "Chen";
    people.age = "31";
    document.write("name: "+people.name+", age: "+people.age); 
    //第二种定义方法
    people = {name:"Wang", age:"33"};
    document.write("name: "+people.name+", age: "+people.age);
</script>
```   
- 使用函数来定义对象，然后创建新的对象实例 <br>
```
<script>
    function people(name,age){
        this.name = name;
        this.age = age;
    }
    son = new people("Wang",1);
    document.write("name:"+son.name+", age:"+son.age);
</script>
```
#### 10.2 String字符串对象
- `String`对象 <br>
String对象用于处理已有的字符串 <br>
字符串可以使用双引号或单引号 <br>
  
- `indexOf()`: 在字符串中查找字符串 <br>
```
<script>
    var str = "Hello world";
    document.write(str.indexOf("world"));
</script>
``` 
- `match()`: 内容匹配 <br>
`document.write(str.match("world"));`
- `replace()`: 替换内容 <br>
`document.write(str.replace("world","JavaScript"));`
- `toUpperCase()和toLowerCase()`: 字符串大小写转换 <br>
```
  document.write(str.toUpperCase());
  document.write(str.toLowerCase());
``` 
- `strong>split()`: 字符串转为数组 <br>
```
  var str = "Hello,My,JavaScript";
  var s = str.split(",");//以逗号作为分割基准
  document.write(s[2]);
``` 
- 其他属性和方法 <br> 
    属性
   - `length`
   - `prototype`
   - `constructor`

    方法
   - `charAt()`
   - `charCodeAt()`
   - `concat()`
   - `fromCharCode()`
   - `lastIndexOf()`
   - `search()`
   - `slice()`
   - `substring()`
   - `substr()`
   - `valueOf()`
#### 10.3 Date日期对象
##### 10.3.1 Date对象
```
<script>
    var date = new Date();
    document.write(date);
</script>
```   
```
执行结果：Mon Sep 14 2020 10:40:42 GMT+0900 (日本标准时间) 
``` 
##### 10.3.2 获得当日的日期
##### 10.3.3 常用方法
- `getFullYear()`: 获取年份 <br>
```
var date = new Date();
document.write(date.getFullYear());
``` 
- `getTime()`: 获取毫秒 <br>
- `setFullYear()`: 设置具体的日期 <br>
- `getDay()`: 获取星期 <br>

```
<body onload="startTime()">
    div id="timetxt"></div>
<script>
    function startTime() {
        var today = new Date();
        var h = today.getHours();
        var m = today.getMinutes();
        var s = today.getSeconds();
        document.getElementById("timetxt").innerHTML = h+":"+m+":"+s;
        t = setTimeout(function () {
            startTime();
            },1000);
        }
</script>
</body>
```
#### 10.4 Array数组对象
##### 10.4.1 Array对象
使用单独的变量名来存储一系列的值
##### 10.4.2 数组的创建
例：`var myArray=["apple","orange","banana"];`
##### 10.4.3 数组的访问
通过指定数组名以及索引号码，可以访问某个特定的元素 <br>
注意：[0]是数组的第一个元素。
##### 10.4.4 数组常用方法
- `concat()`:合并数组 <br>
```
var a = ["apple","orange"];
var b = ["banana","mango"];
var c = a.concat(b);
```  
- `sort()`:排序
升序：<br>
```
var a = ["3","2","4","1","5","9"];
document.write(a.sort()); 
```
降序：<br>
```
var a = ["3","2","4","1","5","9"];
document.write(a.sort(function (a,b) {
    return b-a;
}));
``` 
- `push()`:末尾追加元素 <br>
```
var m = ["a","b"];
m.push("c")
document.write(m);
```
- `reverse()`:数组元素翻转 <br>

```
var m = ["b","a","c","d"]
document.write(m.reverse());
```
#### 10.5 Math对象
##### 10.5.1 Math对象
执行常见的算数任务
##### 10.5.2 常用方法
- `round()`: 四舍五入 <br>
  `document.write(Math.round(3.4));`
- `random()`: 返回0～1之间的随机数 <br>
```
    document.write(Math.random());//0到1的随机数   
    document.write(parseInt(Math.random()*10));//1到10的随机数
```
- `max()`: 返回最高值 <br>
  `document.write(Math.max(10,20,4,2));`
- `min()`: 返回最低值 <br>
  `document.write(Math.min(10,20,4,2));`
- `abs()`: 返回绝对值 <br>
  `document.write(Math.abs(-10));`
### 11. DOM对象控制HTML
#### 11.1 DOM对象控制HTML
##### 11.1.1 方法
- `getElementsByName()`: 获取名字 <br>
```
<p name="pName">Hello</p>
<p name="pName">Hello</p>
<p name="pName">Hello</p>
      
<script>
    function getName() {
        var n = document.getElementsByName("pName");
        var m = n[0];
        m.innerHTML = "Hi";
    }
    getName();
</script>
```
```
执行结果：
 Hi 
 Hello
 Hello
```
- `getElementsByTagName()`: 获取元素 <br>
```
<p name="pName">Hello</p>
<p name="pName">Hello</p>
<p name="pName">Hello</p>
   
<script>
    function getName() {
        var n = document.getElementsByTagName("p");
        var m = n[0];
        m.innerHTML = "Hi";
    }
    getName();
</script>
```
```   
执行结果：
 Hi 
 Hello
 Hello
```
- `getAttribute()`: 获取元素属性 <br>
```
<a id="aID" title="这是a标签的title属性"></a>
<script>
    function getAttr() {
        var anode = document.getElementById("aID");
        var attr = anode.getAttribute("title");
        document.write(attr);
    }
    getAttr();
</script>
```
- `setAttribute()`: 设置元素属性 <br>
```
<a id="aID"></a>
<script>
    function setAttr() {
        var anode = document.getElementById("aID");
        anode.setAttribute("title","这是a标签的title属性");
        var attr = anode.getAttribute("title");
        document.write(attr);
    }
    setAttr();
</script>
```
- `childNodes()`: 访问子节点 <br>
```
<ul>
    <li>apple</li>
    <li>orange</li>
    <li>banana</li>
</ul>
<script>
    function getChildNode() {
        var childnode = document.getElementsByTagName("ul")[0].childNodes;
        alert(childnode.length);
        alert(childnode[0].nodeType);
    }
    getChildNode();
</script>
```  
- `parentNode()`: 访问父节点 <br>
```
<div>
    <p id="pID"></p>
</div>
<script>
    function getParentNode() {
        var pnd = document.getElementById("pID");
        document.write(pnd.parentNode.nodeName);
    }
    getParentNode();
</script>
```
```   
执行结果：DIV
```  
- `createElement()`: 创建元素节点 <br>

```
<body>
<script>
    function createNode() {
        var body = document.body;
        var input = document.createElement("input");
        input.type = "button";
        input.value = "按钮";
        body.appendChild(input); //向末尾插入节点
    }
    createNode();
</script>
</body>
```  
- `createTextNode()`: 创建文本节点 <br>
- `insertBefore()`: 插入节点 <br>
```
<div id="divID">
    <p id="pID">这是div元素的p元素</p>
</div>
<script>
    function insertNode() {
        var div = document.getElementById("divID");
        var node = document.getElementById("pID");
        var newnode = document.createElement("p");
        newnode.innerHTML = "手动插入一个p元素";
        div.insertBefore(newnode,node);
    }
    insertNode();
</script>
``` 
- `removeChild()`: 删除节点 <br>
```
<div id="divID">
    <p id="pID">这是div元素的p元素</p>
</div>
<script>
    function removeNode() {
        var div = document.getElementById("divID");
        var p = div.removeChild(div.childNodes[1]);//删除div的第一个节点
    }
    removeNode();
```
- `offsetHeight()`: 网页尺寸(不包含滚动条) <br>
```
<body>
<script>    
    function getSize() {
        var width = document.body.offsetWidth||document.documentElement.offsetWidth;
        var height = document.body.offsetHeight||document.documentElement.offsetHeight;
        document.write(width+", "+height);
    }
    getSize();
</script>
</body>
```
- `scrollHeight()`: 网页尺寸(包含滚动条) <br>
### 12. JS浏览对象
#### 12.1 Window对象  
##### 12.1.1 window对象
window对象是BOM的核心，window对象指当前的浏览器窗口 <br>
所有JavaScript全局对象，函数以及变量均自动成为window对象的成员 <br>
全局变量是window对象的属性 <br>
全局函数是window对象的方法 <br>
甚至HTML DOM的document也是window对象的属性之一 <br>
##### 12.1.2 window尺寸
`window.innerHeight`: 浏览器窗口的内部高度（不包括工具栏和滚动条）<br>
`window.innerWidth`: 浏览器窗口的内部宽度 <br>
```
<script>
   document.write("宽度："+window.innerWidth+", 高度："+ window.innerHeight);
</script>
```
##### 12.1.3 window方法
- `window.open()`: 打开新窗口 <br>
```
<button id="btn" onclick="btnClick()">提交</button>
<script>
    function btnClick() {
        window.open("OpenWindow.html","windowname","height=200,width=200,top=100,left=100,toolbar=no");
    }
</script>
```
- `window.close()`: 关闭当前窗口 <br>
```
<button id="btn" onclick="btnClick()">提交</button>
<script>
    function btnClick() {
        window.close();
    }
</script>
```
#### 12.2 计时器
##### 12.2.1 计时事件
通过使用JavaScript，可以做到在一个设定的时间间隔之后来执行代码，而不是在函数被调用之后立即执行，我们称之为计时事件
##### 12.2.2 计时方法
- `setInterval()`: 间隔指定的毫秒数不停地执行指定的代码,即让函数不停的执行 <br>
```
<p id="ptime"></p>
<script>
    var mytime = setInterval(function () {
     getTime();
    },1000);
   
    function getTime() {
        var d = new Date();
        var t = d.toLocaleTimeString();//时分秒转换成字符串
        document.getElementById("ptime").innerHTML=t;
    }
</script>
```
- `clearInterval()`: 用于停止`setInterval()`方法执行的函数代码 <br>
```   
<p id="ptime"></p>
<button id="btnID" onclick="stopInterval()">clear</button>
<script>
    var mytime = setInterval(function () {
        getTime();
    },1000);
   
    function getTime() {
        var d = new Date();
        var t = d.toLocaleTimeString();//时分秒转换成字符串
        document.getElementById("ptime").innerHTML=t;
    }
    function stopInterval() {
        clearInterval(mytime);
    }
</script>
```
- `setTimeout()`: 暂停指定的毫秒数后执行指定的代码 <br>
```
<button id="btn" onclick="myTimeout()">延时执行</button>
<script>    
    var win;
    function myTimeout() {
        win = setTimeout(function () {
        alert("hello")},3000); //延时3s执行
    }
</script>
``` 
- `clearTimeout()`: 用于停止执行`setTimeout()`方法的函数代码 <br>
```
<body onload="myTimeout()">
<button id="btn" onclick="stopTimeout()">停止执行</button>
<script>
    var win;
    function myTimeout() {
        alert("hello");
        win = setTimeout(function () {
            myTimeout()},3000);
        }
    function stopTimeout() {
        clearTimeout(win);
    }
</script>
</body>
```
#### 12.3 History对象
##### 12.3.1. History对象
`window.histor`：对象包含浏览器的历史(`url`)的集合
##### 12.3.2 History方法
- `history.back()`: 与在浏览器中点击后退按钮相同 <br>

```
<!--html1-->
<body>
<a href="Browser.html">跳转到后退网页</a>
   
<!--html2-->
<body>
<button id="btn" onclick="goTest()">按钮</button>
<script>
    function goTest() {
        history.back();
    }
</script>
</body>
```
- `history.forward()`: 与在浏览器中点击按钮向前相同 <br>
```
<!--html1-->
<body>
<a href="Browser.html">跳转到后退网页</a>
<button id="btn" onclick="goForward()">按钮</button>
<script>
    function goForward(){
        history.forward();
    }
</script>
   
<!--html2-->
<body>
<button id="btn" onclick="goTest()">按钮</button>
<script>
    function goTest() {
        history.back();
    }
</script>
</body>
```
- `history.go()`: 进入历史中的某个页面 <br>

```
<!--html1-->
<body>
    <a href="History_go.html">跳转到History网页</a>
</body>
   
<!--html2-->
<form>
    <input type="text" id="username">
</form>
    <button id="btn" onclick="safe()">按钮</button>
<script>
    function safe() {
        var name = document.getElementById("username").value;
        if(name=="Chen"){
            history.go(-1);
        }else{
            alert("输入错误！");
        }
    }
</script>
```
#### 12.4 Location对象
##### 12.4.1 Location对象
`window.location`对象用于获得当前页面的地址(URL),并把浏览器重定向到新的页面
##### 12.4.2 Location对象的属性
- `location.hostname`: 返回web主机的域名

```
<button id="btn" onclick="getLocate()">提交</button>
<p id="pID"></p>
<script>
    function getLocate() {
        document.getElementById("pID").innerHTML = window.location.hostname;
    }
</script>
```  
- `location.pathname`: 返回当夜页面的路径和文件名 <br>

```
<button id="btn" onclick="getLocate()">提交</button>
<p id="pID"></p>
<script>
    function getLocate() {
        document.getElementById("pID").innerHTML = window.location.pathname;
    }
</script>
```
- `location.port`: 返回web主机的端口 <br>

```
<button id="btn" onclick="getLocate()">提交</button>
<p id="pID"></p>
<script>
    function getLocate() {
        document.getElementById("pID").innerHTML = window.location.port;
    }
</script>
```  
- `location.protocol`: 返回所使用的web协议(`http://`或`https://`) <br>

```
<button id="btn" onclick="getLocate()">提交</button>
<p id="pID"></p>
<script>
    function getLocate() {
        document.getElementById("pID").innerHTML = window.location.protocol;
    }
</script>
```
- `location.href`: 返回当前页面的url <br>

```
<button id="btn" onclick="getLocate()">提交</button>
<p id="pID"></p>
<script>
    function getLocate() {
        document.getElementById("pID").innerHTML = window.location.href;
    }
</script>
```
- `location.assign()`:加载新的文档 <br>   

```
<button id="btn" onclick="getLocate()">提交</button>
<p id="pID"></p>
<script>
    function getLocate() {
        location.assign("http://www.google.co.jp");
    }
</script>  
```
#### 12.5 Screen对象 
##### 12.5.1 Screen对象
window.screen对象包含有关用户屏幕的信息
##### 12.5.2 属性
- `screen.availWidth`: 可用的屏幕宽度 
- `screen.availHeight`: 可用的屏幕高度
- `screen.Height`: 屏幕高度
- `screen.Width`: 屏幕宽度
##### 12.5.3 例子
```
<script>
    document.write("可用高度："+screen.availHeight+", 可用宽度"+screen.availWidth);
    document.write("高度："+screen.height+", 宽度"+screen.width);
</script>
```
### 13.JS面向对象
#### 13.1 认识面向对象
##### 13.1.1 面向对象中的概念
- 一切事物皆对象
- 对象具有封装和继承特性
- 信息隐藏
#### 13.2 基本面向对象
```
var person={
    name:"Chen",
    age: 31,
    writeCode:function () {
        alert("写代码");
    }
}
alert(person.writeCode());
```
#### 13.3 函数构造器构造对象
```
function Person() {

}
Person.prototype={
    name: "Wang",
    age: 33,
    writeCode:function () {
        alert("写代码");
    }
}
var p = new Person();
p.age
p.name
p.writeCode()
```
#### 13.4 深入JavaScript面向对象
##### 13.1 面向对象（1）
- 创建一个子类
```
function People() {
    
}
People.prototype.say = function () {
    alert("peo-hello");
}
function Student() {

}
Student.prototype = new People();
var s = new Student();
s.say();
```
```
执行结果：peo-hello
```
- 复写父类的方法
```
function People() {
    
}
People.prototype.say = function () {
    alert("peo-hello");
}
function Student() {

}
Student.prototype = new People();
var superSay = Student.prototype.say;
Student.prototype.say = function () {
    superSay.call(this);
    alert("stu-hello");
}
var s = new Student();
s.say();
```
```
执行结果：
 peo-hello 
 stu-hello
```
- 传参
```
function People(name) {
    this._name = name;
}
People.prototype.say = function () {
    alert("peo-hello: "+this._name);
}
function Student(name) {
    this._name = name;
}
Student.prototype = new People();
var superSay = Student.prototype.say;
Student.prototype.say = function () {
    superSay.call(this);
    alert("stu-hello: "+this._name);
}
var s = new Student("Chen");
s.say();
```
```
执行结果：
 peo-hello: Chen 
 stu-hello: Chen
```
- 封装
```
(function (){
    var n = "Cuncun";
    function People(name) {
        this._name = name;
    }
    People.prototype.say = function () {
        alert("peo-hello: "+this._name+" "+n);
    }
    window.People = People;
}());

(function () {
    function Student(name) {
        this._name = name;
    }
    Student.prototype = new People();
    var superSay = Student.prototype.say;
    Student.prototype.say = function () {
        superSay.call(this);
        alert("stu-hello: "+this._name+" "+n); //无法访问n，因为n已被父类封装
    }
    window.Student = Student;
}())

var s = new Student("Chen");
s.say();
```
```
执行结果：peo-hello: Chen Cuncun
```
##### 13.2 面向对象（2）
- 创建类
```
//创建一个类
function Person() {
    var _this = {}
    _this.sayHello = function () {
        alert("P-Hello");
    }
    return _this;
}
//继承Person类
function Teacher() {
    var _this = Person();
    return _this;
}
var t = new Teacher();
t.sayHello();
```
```
执行结果：P-Hello
```
- 复写父类中的属性
```
//创建一个类
function Person() {
    var _this = {}
    _this.sayHello = function () {
        alert("P-Hello");
    }
    return _this;
}
//继承Person类
function Teacher() {
    var _this = Person();
    _this.sayHello = function () {
        alert("T-Hello");
    }
    return _this;
}
var t = new Teacher();
t.sayHello();
```
```
执行结果：T-Hello
```
- 调用父类中的方法
```
//创建一个类
function Person() {
    var _this = {}
    _this.sayHello = function () {
        alert("P-Hello");
    }
    return _this;
}
//继承Person类
function Teacher() {
    var _this = Person();
    var superSay = _this.sayHello;
    _this.sayHello = function () {
        superSay.call(_this);
        alert("T-Hello");
    }
    return _this;
}
var t = new Teacher();
t.sayHello();
```
```
执行结果：
 P-Hello
 T-Hello
```
- 传参
```
//创建一个类
function Person(name) {
    var _this = {}
    _this.name = name;
    _this.sayHello = function () {
        alert("P-Hello: "+_this.name);
    }
    return _this;
}
//继承Person类
function Teacher(name) {
    var _this = Person(name);
    var superSay = _this.sayHello;
    _this.sayHello = function () {
        superSay.call(_this);
        alert("T-Hello: "+_this.name);
    }
    return _this;
}
var t = new Teacher("Chen");
t.sayHello();
```
```
执行结果：
  P-Hello: Chen 
  T-Hello: Chen
```
- 封装
```
//封装一个类
(function (){
    var n = "Cuncun";
    function Person(name) {
        var _this = {}
        _this.name = name;
        _this.sayHello = function () {
            alert("P-Hello: "+_this.name +" "+n);
        }
        return _this;
    }
    window.Person = Person;
}())

//继承Person类
function Teacher(name) {
    var _this = Person(name);
    var superSay = _this.sayHello;
    _this.sayHello = function () {
        superSay.call(_this);
        alert("T-Hello: "+_this.name+n); //无法访问n，因为n已被父类封装
    }
    return _this;
}
var t = new Teacher("Chen");
t.sayHello();
```
```
执行结果：P-Hello: Chen Cuncun
```


 

 
 