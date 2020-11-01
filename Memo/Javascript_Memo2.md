# Javascript
## 1. 基础
### 1.1 简介
一个完整的javascript实现应该由以下三个部分构成：<br/>
- ECMAScript
- DOM
- BOM
### 1.2 特点
- 解释型语言
- 类似于C和Java语法结构
- 动态语言
- 基于原型的面向对象
### 1.3 指令
- `alert`：控制浏览器弹出一个警告框
  - `alert("这是一个警告！");`
- `document.write()`：让计算机在页面中(即body)输出一个内容
  - `document.write("此内容会显示在网页中");`
- `console.log()`：向控制台输出一个内容
  - `console.log("向控制台输出一个内容");`
### 1.4 js编写位置
- 可以将js代码编写到标签的`onclick`属性中，当点击按钮时，js代码才会被执行
```
<body>
    <button onclick="alert('已被点击');">点击</button>
</body>
```
- 可以将js代码编写在超链接的`href`属性中，当点击超链接时，会执行js代码
```
<body>
    <a href="javascript:alert('已被点击');">点击</a>
</body>
```
- 注意：虽然可以写在标签的属性中，但是他们属于结构与行为耦合，不方便维护，不推荐使用
- 可以将js代码编写到`script`标签
```
<script>
    alert("这是script标签中的代码");
</script>
```
- 可以将js代码编写到外部js文件中，然后通过`script`标签引入 <br/>
写到外部文件中可以在不同的页面中同时引用，也可以利用浏览器的缓存机制（推荐使用的方式）<br/>
  - 注意：`script`标签一旦用于引入外部文件了，就不能在此`script`标签中编写代码了，即使编写了浏览器也会忽略。<br/>
  - 如果需要则可以再创建一个新的`script`标签用于编写内部代码
```
<script type="text/javascript" src="demo1.js"></script>
```
以下是`demo1.js`文件
```
alert("这是外部js文件的警告");
```
### 1.5 基本语法
- 注释
  - `//`：单行注释
  - `/**/`：多行注释
- js中严格区分大小写
- 每条语句以分号`;`结尾
- js中会忽略多个空格和换行，所以可以利用空格和换行对代码进行格式化
### 1.6 字面量和变量
#### 1.6.1 字面量
字面量都是一些不可改变的值(比如：1 2 3 4 5) <br/>
字面量都是可以直接使用，但是一般不会直接使用字面量
#### 1.6.2 变量
变量可以用来保存字面量，而且变量的值是可以任意改变的 <br/>
变量更加方便我们使用，所以在开发中都是通过变量取保存一个字面量，而很少直接使用字面量 <br/>
- 声明变量：在js中使用`var`关键字来声明一个变量
```
//声明变量
var a;
//为变量赋值
a = 123;
//在控制台中输出变量a
console.log(a);
```
```
//声明和赋值同时进行
var b = 456;
//在控制台中输出变量b
console.log(b);
```
- 可以通过变量对字面量进行描述
```
var age = 80;
```
### 1.7 标识符
在js中所有的可以由我们自主命名的都可以称为是标识符。<br/>
例如：变量名，函数名，属性名都属于标识符。 <br/>
命名一个标识符需要遵守如下的规则：<br/>
- 标识符可以含有字母，数字，`_`，`$`
  - `var a_1_$ = 123;`
- 标识符不能以数字开头
- 标识符不能是ES中的关键字或保留字
- 标识符一般都采用驼峰命名法
  - 首字母小写，每个单词的开头字面大写，其余字面小写
  - 例如：`helloWorld`
- js底层保存标识符时实际上是采用的Unicode编码，所以理论上讲，所有的utf-8中含有的内容都可以作为标识符
### 1.8 数据类型
数据类型指的就是字面量的类型。在js中一共有六种数据类型。<br/>
- 基本数据类型
  - `String`：字符串
  - `Number`：数值
  - `Boolean`：布尔值
  - `Null`：空值
  - `Undefined`：未定义
- 引用数据类型
  - `Object`：对象
#### 1.8.1 `String`：字符串
- 在js中字符串需要使用引号引起来。
- 使用双引号或单引号都可以，但是不能混着用。
- 引号不能嵌套，`“`不能放`”`，`‘`不能放`’`。
```
var str = "hello";
console.log(str);
```
- 在字符串中可以使用`\`作为转义字符，当表示一些特殊符号时可以使用`\`进行转义 <br/>
`str = "She said: \"Today is her birthday.\"";`
- `\n`：表示换行
- `\t`：制表符(相当于按了Tab键)
- `\\`：表示`\`
#### 1.8.2 `Number`：数字型
在js中所有的数值都是Number类型，包括整数和浮点数。<br/>
可以使用一个运算符`typeof`来检查一个变量的类型。<br/>
- 检查字符串时，会返回`string`
- 检查数值时，会返回`number`
- 语法：`typeof 变量` 
```
var a = 123;
var b = "123";
console.log(typeof a);
console.log(typeof b);
```
- js中可以表示的数字的最大值：`Number.MAX_VALUE`，最大值：1.7976931348623157e+308
- js中可以表示大于0的最小值：`Number.MIN_VALUE`，最小值：5e-324
- 如果使用`Number`表示的数字超过了最大值，则会返回一个`Infinity`，表示正无穷
  - `Infinity`，表示正无穷
  - `-Infinity`，表示负无穷
  - `Infinity`是一个字面量，可以直接`a = Infinity`来定义。
  - 使用`typeof`检查`Infinity`也会返回`number`类型
- `NaN`：是一个特殊的数字，表示`Not A Number`
  - `a = NaN;`
  - 使用`typeof`检查一个`NaN`，也会返回`number`类型
```
a = "abc" * "bcd"
console.log(a);

实行结果：
NaN
```
```
a = NaN
console.log(typeof a);  

实行结果：
number
```
- 在js中整数的运算基本可以保证精确。
- 如果使用js进行浮点元素，可以得到一个不精确的结果，所以千万不要使用js进行对精确度要求比较高的运算。
#### 1.8.3 `boolean`：布尔值
布尔值只有两个，主要用来做逻辑判断。<br/>
- `true`：表示真
- `false`：表示假
- 使用`typeof`检查一个布尔值时，会返回`boolean`
#### 1.8.4 `Null`：空值
`Null`类型的值只有一个，就是`null`。<br/>
- `null`专门用来表示一个为空的对象。
- 使用`typeof`检查一个`null`值时，会返回`object`。
#### 1.8.5 `Undefined`：未定义
`Undefined`类型的值只有一个，就是`undefined`。<br/>
- 当声明一个变量，但是并不给变量赋值时，它的值就是`undefined`。
- 使用`typeof`检查一个`undefined`值时，会返回`undefined`。
### 1.9 强制类型转换
将一个数据类型强制转换为其他的数据类型。<br/>
类型转换主要指，将其他的数据类型转换为：`String` `Number` `Boolean` <br/>
#### 1.9.1 将其他的数据类型转换为`String`
- 转换方式(1)
  - 调用被转换数据类型的`toString()`方法，该方法不会影响到原变量，它会将转换的结果返回
  - 注意：`null`和`undefined`这两个值没有`toString()`方法，所以如果调用他们的方法，会报错 <br/>
例子1：
```  
var a = 123;
//调用a的toString()方法
a.toString();

console.log(typeof a);

实行结果：
number
```
例子2：
```  
var a = 123;
//调用a的toString()方法
var b = a.toString();

console.log(typeof b);

实行结果：
string
```
例子3：
```  
var a = 123;
//调用a的toString()方法
a = a.toString();

console.log(typeof a);

实行结果：
string
```
- 转换方式(2)
  - 调用`String()`函数，并将被转换的数据作为参数传递给函数。该方法不会影响到原变量，它会将转换的结果返回
  - 使用`String()`函数做强制类型转换时：
    - 对于`Number`和`Boolean`实际上就是调用的`toString()`方法
    - 但是对于`null`和`undefined`，就不会调用`toString()`方法，它会将`null`直接转换为`“null”`，将`undefined`直接转换为`”undefined“` <br/>
例子1：
```
a = 123;
//调用String()函数，来将a转换为字符串
a = String(a);
console.log(typeof a);

实行结果：
string
```
例子2：
```
a = null;
a = String(a);

console.log(typeof a);

实行结果：
string
```
#### 1.9.2 将其他的数据类型转换为`Number`
- 转换方式(1)：使用`Number()`函数
  - 字符串 --> 数字
    - 如果是纯数字的字符串，则直接将其转换为`number`
    - 如果字符串中有非数字的内容，则转换为`NaN`
    - 如果字符串是一个空串或者是一个全是空格的字符串，则转换为`0`
  - 布尔 --> 数字
    - `true` 转成 `1`
    - `false` 转成 `0`
  - `null` --> 数字：`0`
  - `undefined`--> 数字：`NaN` <br/>
例子1：
```
a = “123”;
//调用Number()函数来将a转换为Number类型
a = Number(a);

console.log(typeof a);
console.log(a);

实行结果：
number
123
```
例子2：
```
a = “123abc”;
//调用Number()函数来将a转换为Number类型
a = Number(a);

console.log(typeof a);
console.log(a);

实行结果：
number
NaN
```
例子3：
```
a = “”;
//调用Number()函数来将a转换为Number类型
a = Number(a);

console.log(typeof a);
console.log(a);

实行结果：
number
0
```
例子4：
```
a = null;
//调用Number()函数来将a转换为Number类型
a = Number(a);

console.log(typeof a);
console.log(a);

实行结果：
number
0
```
- 转换方式(2)：这种方式专门用来对付字符串 <br/>
  - `parseInt()`函数：把一个字符串转换为一个整数
  - `parseFloat()`函数：把一个字符串转换为一个浮点数
  - 注意：如果对非`String`使用`parseInt()`或`parseFloat()`，它会先将其转换为`String`，然后再操作
例子1：
```
a = “123px”;
//parseInt()可以将一个字符串中的有效的整数内容取出来，然后转换成Number
a = parseInt(a);

console.log(typeof a);
console.log(a);

实行结果：
number
123
```
例子2：
```
a = “123.456px”;
//parseFloat()作用和parseInt()类似，不同的是它可以获得有效的小数
a = parseFloat(a);

console.log(typeof a);
console.log(a);

实行结果：
number
123.456
```

