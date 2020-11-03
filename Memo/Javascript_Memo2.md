# Javascript基础
## 1. 简介
一个完整的javascript实现应该由以下三个部分构成：<br/>
- ECMAScript
- DOM
- BOM
## 2. 特点
- 解释型语言
- 类似于C和Java语法结构
- 动态语言
- 基于原型的面向对象
## 3. 指令
- `alert`：控制浏览器弹出一个警告框
  - `alert("这是一个警告！");`
- `document.write()`：让计算机在页面中(即body)输出一个内容
  - `document.write("此内容会显示在网页中");`
- `console.log()`：向控制台输出一个内容
  - `console.log("向控制台输出一个内容");`
## 4. js编写位置
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
## 5. 基本语法
- 注释
  - `//`：单行注释
  - `/**/`：多行注释
- js中严格区分大小写
- 每条语句以分号`;`结尾
- js中会忽略多个空格和换行，所以可以利用空格和换行对代码进行格式化
## 6. 字面量和变量
### 6.1 字面量
字面量都是一些不可改变的值(比如：1 2 3 4 5) <br/>
字面量都是可以直接使用，但是一般不会直接使用字面量
### 6.2 变量
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
## 7. 标识符
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
## 8. 数据类型
数据类型指的就是字面量的类型。在js中一共有六种数据类型。<br/>
- 基本数据类型
  - `String`：字符串
  - `Number`：数值
  - `Boolean`：布尔值
  - `Null`：空值
  - `Undefined`：未定义
- 引用数据类型
  - `Object`：对象
#### 8.1 `String`：字符串
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
### 8.2 `Number`：数字型
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
### 8.3 `boolean`：布尔值
布尔值只有两个，主要用来做逻辑判断。<br/>
- `true`：表示真
- `false`：表示假
- 使用`typeof`检查一个布尔值时，会返回`boolean`
### 8.4 `Null`：空值
`Null`类型的值只有一个，就是`null`。<br/>
- `null`专门用来表示一个为空的对象。
- 使用`typeof`检查一个`null`值时，会返回`object`。
### 8.5 `Undefined`：未定义
`Undefined`类型的值只有一个，就是`undefined`。<br/>
- 当声明一个变量，但是并不给变量赋值时，它的值就是`undefined`。
- 使用`typeof`检查一个`undefined`值时，会返回`undefined`。
## 9. 强制类型转换
将一个数据类型强制转换为其他的数据类型。<br/>
类型转换主要指，将其他的数据类型转换为：`String` `Number` `Boolean` <br/>
### 9.1 将其他的数据类型转换为`String`
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
### 9.2 将其他的数据类型转换为`Number`
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
a = "123";
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
a = "123abc";
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
a = "";
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
  - 注意：如果对非`String`使用`parseInt()`或`parseFloat()`，它会先将其转换为`String`，然后再操作 <br/>

例子1：
```
a = "123px";
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
a = "123.456px";
//parseFloat()作用和parseInt()类似，不同的是它可以获得有效的小数
a = parseFloat(a);

console.log(typeof a);
console.log(a);

实行结果：
number
123.456
```
### 9.3 将其他的数据类型转换为`Boolean`
- 转换方式(1)：使用`Boolean()`函数 
  - 数字 --> 布尔
    - 除了`0`和`NaN`，其余的都是`true`
  - 字符串 --> 布尔
    - 除了空串，其余的都是`true`
  - `null`和`undefined`都会转换为`false`
  - 对象也会转换为`true`
```
var a = 123;

//调用Boolean()函数来将a转换为布尔值
a = Boolean(a);

console.log(typeof a);
console.log(a);

实行结果：
boolean
true
```
- 转换方式(2)：隐式类型转换
  - 为任意的数据类型做两次非运算，即可讲其转换为布尔值
```
var a = "hello";
a = !!a; //true

console.log(typeof a);

实行结果：
boolean
true
```
## 10. 其他进制的数字
- 在js中，如果需要表示16进制的数字，则需要以`0x`开头。
```
a = 0x10; --> 16
a = 0xff; --> 255
```
- 在js中，如果需要表示8进制的数字，则需要以`0`开头。
```
a = 070; --> 56
```
- 在js中，如果需要表示2进制的数字，则需要以`0b`开头，但不是所有的浏览器都支持。<br/>
有些浏览器会当成8进制解析，有些会当成10进制解析。
```
a = 0b10; --> 2
```
```
a = "070";
 
//可以在parseInt()中传递一个第二个参数，来指定数字的进制。
a = parseInt(a,10);
```
## 11. 算数运算符
运算符也叫操作符，通过运算符可以对一个或多个值进行运算，并获取运算结果。<br/>
比如：`typeof`就是一个运算符，可以来获得一个值的类型。 <br/>
它会将该值的类型以字符串的形式返回：`number` `string` `boolean` `undefined` `object`<br/>
当对非`Number`类型的值进行运算时，会将这些值转换为`Number`，然后再运算。<br/>
任何值和`NaN`做运算结果都是`NaN`。
- `+` 可以对两个值进行加法运算，并将结果返回。
  - 如果对两个字符串进行加法运算，则会做拼串，会将两个字符串拼接为一个字符串，并返回
  - 任何值和字符串做加法运算，都会先转换为字符串，然后再和字符串做拼串的操作。
    - 我们可以利用这一特点，来将一个任意的数据类型转换为`String`。
    - 我们只需要为任意的数据类型`+`一个`""`即可将其转换为`String`。 
    - 这是一个隐式的类型转换，有浏览器自动完成，实际上它也是调用`String()`函数。
例子1：
```
result = true + "hello"

实行结果：
truehello
```
例子2：
```
var a = 123;
a = a + "";

console.log(typeof c);
console.log(c);

实行结果：
string
123
```
- `-` 可以对两个值进行减法运算，并将结果返回。
- `*` 可以对两个值进行乘法运算，并将结果返回。
- `/` 可以对两个值进行除法运算，并将结果返回。
  - 任何值做`-` `*` `/`运算时都会自动转换为`Number`。
  - 我们可以利用这一特点做隐式的类型转换。
  - 可以通过`一个值 - 0` `一个值 * 1` `一个值 / 1`来将其转换为`Number`。
  - 原理和`Number()`函数一样，使用起来更加简单。
```
var a = "123";
a = a - "";

console.log(typeof a);
console.log(a);

实行结果：
number
123
```
- `%` 可以对两个值进行取余数运算，并将结果返回。
## 12. 一元运算符
只需要一个操作数。<br/>
- `+` 正号：不会对数字产生任何影响
- `-` 负号：可以对数字进行负号的取反
- 对于非`Number`类型的值：
  - 它会将其先转换为`Number`，然后再运算
  - 可以对一个其他的数据类型使用`+`，来将其转换为`number`
  - 它的原理和`Number()`函数一样

例子1：
```
a = "18";
a = +a;

console.log("a = " + a);
console.log(typeof a);

实行结果：
a = 18
number
```
例子2：
```
var result = 1 + +"2" +3;

console.log("result = " + result);
console.log(typeof result);

实行结果：
a = 6
number
```
## 13. 自增和自减
### 13.1 自增
- 通过自增可以使变量在自身的基础上增加1
- 对于一个变量自增以后，原变量的值会立即自增1
- 自增分成两种：`后++`(`a++`)和`前++`(`++a`)
  - 无论是`a++`还是`++a`，都会立即使原变量的值自增1
  - 不同的是`a++`和`++a`的值不同
- `a++`的值等于原变量的值(自增前的值)
- `++a`的值等于原变量的新值(自增后的值)
```
var d = 20;

//20 + 22 + 22
var result = d++ + ++d +d
console.log("result = " + result);

实行结果：
result = 64
``` 
### 13.2 自减
- 通过自减可以使变量在自身的基础上减1
- 对于一个变量自减以后，原变量的值会立即自减1
- 自减分成两种：`后--`(`a--`)和`前--`(`--a`)
  - 无论是`a--`还是`--a`，都会立即使原变量的值自减1
  - 不同的是`a--`和`--a`的值不同
- `a--`的值等于原变量的值(自减前的值)
- `--a`的值等于原变量的新值(自减后的值)
### 13.3 练习
```
var n1 = 10;
var n2 = 20;

var n = n1++; //n1 = 11, n1++ = 10
console.log('n = ' + n); //10
console.log('n1 = ' + n1); //11

n = ++n1; //n = 12, ++n1 = 12
console.log('n = ' + n); //12
console.log('n1 = ' + n1); //12

n = n2--; //n2 = 19, n2-- = 20
console.log('n = ' + n); //20
console.log('n2 = ' + n2);//19

n = --n2; //n = 18, n2 = 18
console.log('n = ' + n); // 18
console.log('n2 = ' + n2); // 18
```
## 14. 逻辑运算符
### 14.1 `!` 非
可以用来对一个值进行非运算，所谓非运算就是值对一个布尔值进行取反操作。 <br/>
- `true`变`false`，`false`变`true`
- 如果对一个值进行两次取反，它不会变化。
- 如果对非布尔值进行运算，则会将其转换为布尔值，然后再取反
  - 所以我们可以利用该特点，来将一个其他的数据类型转换为布尔值
  - 可以为一个任意数据类型取两次反，来将其转换为布尔值
  - 原理和`Boolean()`函数一样 <br/>

例子1：
```
var b = 10;
b = !b;

console.log("b = " + b);
console.log(typeof b);

实行结果：
b = false
boolean
```
例子2：
```
var b = 10;
b = !!b;

console.log("b = " + b);
console.log(typeof b);

实行结果：
b = true
boolean
```
### 14.2 `&&` 与
可以对符号两侧的值进行与运算，并返回结果。<br/>
运算规则：两个值中只要有一个值为`false`就返回`false`。<br/>
js中的"与"属于短路的"与"，如果第一个值为`false`，不会检查第二个。
### 14.3 `||` 或
可以对符号两侧的值进行或运算，并返回结果。<br/>
运算规则：两个值中只要有一个值为`true`就返回`true`。<br/>
如果两个值都为`false`，才返回`false`。<br/>
js中的"或"属于短路的"或"，如果第一个值为`true`，则不会检查第一个。<br/>
第一个值为`false`，才会检查第二个。
## 15. 非布尔值的与或运算
对于非布尔值进行与或运算是，会先将其转换为布尔值，然后再运算，并且返回原值<br/>
- 如果两个值都为`true`，则返回后边的
```
var result = 1 && 2;
console.log("result = "+result);

实行结果：
result = 2
```
- 如果两个值中有`false`，则返回靠前的`false`
```
var result = NaN && 0; 
console.log("result = "+result);

实行结果：
result = NaN
```
### 15.1 与运算
- 如果第一个值为`true`，则必然返回第二个值
- 如果第一个值为`false`，则必然返回第一个值
### 15.2 或运算
- 如果第一个值为`true`，则必然返回第一个值
- 如果第一个值为`false`，则必然返回第二个值
## 16. 赋值运算符
- `=`：可以将符号右侧的值赋值给符号左侧的变量。
- `+=`：`a += 5;` 等价于 `a = a + 5;`
- `-=`：`a -= 5;` 等价于 `a = a - 5;`
- `*=`：`a *= 5;` 等价于 `a = a * 5;`
- `/=`：`a /= 5;` 等价于 `a = a / 5;`
- `%=`：`a %= 5;` 等价于 `a = a % 5;`
## 17. 关系运算符
通过关系运算符可以比较两个值之间的大小。<br>
如果关系成立它会返回`true`，如果关系不成立则会返回`false`。<br/>
- `>` 大于号
  - 判断符号左侧的值是否大于右侧的值
  - 如果关系成立，返回`true`，如果关系不成立则返回`false`
- `>=` 大于等于号
  - 判断符号左侧的值是否大于或等于右侧的值
- `<` 小于号
- `<=` 小于等于号
- 非数值的情况
  - 对于非数值进行比较时，会将其转换为数字然后再比较
  - 任何值和`NaN`做比较都是`false`
  - 如果符号两侧的值都是字符串时，不会将其转换为数字进行比较，而会分别比较字符串中字符的Unicode编码
  - 如果比较的两个字符串的数字，可能会得到不可预期的结果。
  - 注意：在比较两个字符串型的数字时，一定要转型
```
console.log(1 >= true); //true
console.log(1 > "0"); //true
console.log(10 > null); //true

//任何值和NaN做比较都是false
console.log(10 > "hello"); //false
console.log(true > false); //true

//比较两个字符串时，比较的是字符串的字符编码
//如果两位一样，则比较下一位，所以借用它来对英文进行排序
console.log("a" > "b"); //false

console.log("133123454765" > +"5"); //false
```
## 17. Unicode编码表
- 在js中使用转义字符输入Unicode编码：`\u四位编码` 这里的编码需要的是16进制
- 在网页中使用Unicode编码：`&#编码` 这里的编码需要的是10进制
## 18. 比较运算符 
### 18.1 相等运算符 `==`
比较两个值是否相等，如果相等返回`true`，否则返回`false` <br/>
- 当使用`==`来比较两个值时，如果值的类型不同，则会自动进行类型转换，将其转换为相同的类型，然后再比较。
```
console.log("1" == 1); //true

//将布尔值和字符串都转换成Number类型
console.log(true == "1"); //true
console.log(null == 0); //false
```
- `undefined` 衍生自`null`，所以这两个值做相等判断时，会返回`true`
- `NaN`不和任何值相等，包括它本身
```
console.log(NaN == undefined); //false
console.log(NaN == NaN); //false
```
- 可以通过`isNaN()`函数来判断一个值是否是`NaN`
  - 如果该值是`NaN`，则返回`true`，否则返回`false`
```
var b = NaN;
console.log(isNaN(b)); //true
```
### 18.2 不相等运算符 `!=`
不相等用来判断两个值是否不相等，如果不相等返回`true`，否则返回`false`。<br/>
- 不相等也会对变量进行自动的类型转换，如果转换后相等它也会返回`false`。
### 18.3 其他比较运算符
- `===` 全等
  - 用来判断两个值是否全等，它和相等类似，不同的是它不会做自动的类型转换 
    - 如果两个值的类型不同，直接返回`false`
```
console.log("123" === 123); //false
console.log(null === undefined); //false
```
- `!==` 不全等
  - 用来判断两个值是否不全等，和不等类似，不同的是它不会做自动的类型转换
    - 如果两个值的类型不同，则会返回`true`
## 19. 条件运算符
条件运算符也叫三元运算符。