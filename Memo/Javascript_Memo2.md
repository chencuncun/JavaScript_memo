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
    - 但是对于`null`和`undefined`，就不会调用`toString()`方法，它会将`null`直接转换为`"null"`，将`undefined`直接转换为`"undefined"` <br/>

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
    - 这是一个隐式的类型转换，有浏览器自动完成，实际上它也是调用`String()`函数。 <br/>

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
对于非布尔值进行与或运算时，会先将其转换为布尔值，然后再运算，并且返回原值<br/>
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
条件运算符也叫三元运算符。<br/>
- 语法：`条件表达式?语句1:语句2;` <br/>
- 执行的流程
  - 条件运算符在执行时，首先对条件表达式进行求值
  - 如果该值为`true`，则执行语句1，并返回执行结果
  - 如果该值为`false`，则执行语句2，并返回执行结果 <br/>

例子1：
```
//获取a和b中的最大值
var a = 30;
var b = 40;
var max = a > b ? a : b;
```
例子2：
```
//获取a，b，c中的最大值
var a = 30;
var b = 40;
var c = 50;

//获取a和b中的最大值
var max = a > b ? a : b;
//获取a b c中的最大值
max = max > c ? max : c;
```
  - 如果条件的表达式的求值结果是一个非布尔值，会将其转换为布尔值然后再运算。<br/>

例子3：
```
"hello"?alert("语句1"):alert("语句2"); //语句1
""?alert("语句1"):alert("语句2"); //语句2
```
## 20. 运算符的优先级
- `,`运算符：可以分割多个语句，一般可以在声明多个变量时使用。
```
//可以同时声明多个变量并赋值
var a = 1 , b = 2, c = 3;
```
- 在js中运算符也有优先级，比如先乘除后加减。
  - 在js中有一个运算符优先级的表，在表中越靠上优先级越高，优先级越高越优先计算
  - 如果优先级一样，则从左往右运算。
  - 如果遇到优先级不清楚的，可以使用()来改变优先级。
## 21. 代码块
js中的代码块，只具有分组的作用，没有其他的用途。代码块内的内容，在外部是完全可见的。
## 22. 流程控制语句
### 22.1 条件判断语句: if语句
使用条件判断语句可以在执行某个语句之前进行判断，如果条件成立才会执行语句，条件不成立则语句不执行。<br/>
- 语法1：
```
if(条件表达式){
    语句...
}
```
if语句在执行时，会先对条件表达式进行求值判断。<br/>
  - 如果条件表达式的值为`true`，则执行`if`后的语句。
  - 如果条件表达式的值为`false`，则不会执行`if`后的语句。

- 语法2：
```
if(条件表达式){
    语句...
}else{
    语句...
}
```
当该语句执行时，会先对if后的条件表达式进行求值判断。<br/>
  - 如果该值是`true`，则执行`if`后的语句
  - 如果该值是`false`，则执行`else`后的语句

- 语法3：
```
if(条件表达式){
    语句...
}else if(条件表达式){
    语句...
}else if(条件表达式){
    语句...
}else{
    语句...
}
```
当该语句执行时，会从上到下依次对条件表达式进行求值判断。<br/>
  - 如果值为`true`，则执行当前语句。
  - 如果值为`false`，则继续向下判断。
  - 如果所有的条件都不满足，则执行最后一个`else`语句。
  - 该语句中，只会有一个代码块被执行，一旦代码块执行了，则直接结束语句

- 练习
  - `prompt()`：可以弹出一个提示框，该提示框中会带有一个文本框
    - 用户可以在文本框中输入一段内容，该函数需要一个字符串作为参数，
    - 该字符串将会作为提示框的提示文字
    - 用户输入的内容将会作为函数的返回值返回，可以定义一个变量来接收该内容

例子1：
```
输入期末考试成绩：
如果成绩为100，输出“奖励一辆BMW”；
如果成绩在80以上99以下，输出“奖励一台iphone15s”；
如果成绩在60以上，79以下，输出“奖励一本参考书”；
如果成绩在59以下，输出“什么奖励也没有”
<script>
    var score = prompt("从键盘输入小明的期末成绩：");
    if (score > 100 || score < 0 || isNaN(score)) {
        alert("请输入正确的分数！");
    } else {
        if (score == 100) {
            alert("奖励一辆BMW");
        } else if (score >= 80) {
            alert("奖励一台iphone15s");
        } else if (score >= 60) {
            alert("奖励一本参考书");
        } else {
            alert("什么奖励也没有");
        }
    }    
</script>
```
例子2：
```
输入三个数字，再将其从小到大排列
<script>
      //prompt()函数的返回值是String类型
      //将String类型前面加+，即可将String类型转Number类型
      var num1 = + prompt("请输入第一个整数：");
      var num2 = + prompt("请输入第二个整数：");
      var num3 = + prompt("请输入第三个整数：");

      if (num1 < num2 && num1 < num3) {
          //num1最小
          if (num2 < num3) {
            //num1最小，num2 中间，num3最大
            alert(num1 + "," + num2 + "," + num3);
          } else {
            //num1最小，num3 中间，num2最大
            alert(num1 + "," + num3 + "," + num2);
          }
      } else if (num2 < num1 && num2 < num3) {
          //num2最小
          if (num1 < num3) {
            //num2最小，num1中间，num3最大
            alert(num2 + "," + num1 + "," + num3);
          } else {
            //num2最小，num3中间，num1最大
            alert(num2 + "," + num3 + "," + num1);
          }
      } else {
          //num3最小
          if (num1 < num2) {
            //num3最小，num1中间，num2最大
            alert(num3 + "," + num1 + "," + num2);
          } else {
            //num3最小，num2中间，num1最大
            alert(num3 + "," + num2 + "," + num3);
          }
      }
</script>
```
### 22.2 条件分支语句: switch语句
- 语法：
```
switch(条件表达式){
  case 表达式:
    语句...
    break;
  case 表达式:
    语句...
    break;
  case 表达式:
    语句...
    break;
  default:
    语句...
    break;
}
```
- 执行流程：`switch...case... 语句`
  - 在执行时会依次将`case`后的表达式的值和`switch`后的条件表达式的值进行全等比较
    - 如果比较结果为`true`，则从当前`case`处开始执行代码
    - 如果比较结果为`false`，则继续向下比较
    - 如果所有的比较结果都为`false`，则只执行`default`后的语句

例子1:
```
var num = 3;
switch(num){
  case 1: 
    console.log("壹");
    //使用break可以退出switch语句
    break;
  case 2: 
    console.log("贰");
    break;
  case 3: 
    console.log("叁");
    break;
  default:
    console.log("非法数字");
    break;
}
```
例子2：
```
分数大于等于60为合格，否则为不合格
var score = 55;

switch(parseInt(score/10)){
  case 10:
  case 9:
  case 8:
  case 7:
  case 6:
    console.log("合格");
    break;
  default:
    console.log("不合格");
    break;
}
``` 
```
var score = 55;

switch(true){
  case score >= 60:
    console.log("合格");
    break;
  default:
    console.log("不合格");
    break;
}
```
### 22.3 循环语句
通过循环语句可以反复的执行一段代码多次
### 22.3.1 while循环
- 语法：
```
while(条件表达式){
  语句...
}
```
- `while`语句在执行时：
  - 先对条件表达式进行求值判断
    - 如果值为`true`，则执行循环体，循环体执行完毕后，继续对表达式进行判断
    - 如果值为`true`，则继续执行循环体，依次类推
    - 如果值为`false`，则终止循环   
  - 创建一个循环，往往需要三个步骤
    - 初始化一个变量
    - 在循环中设置一个条件表达式
    - 定义一个更新表达式，每次更新初始化变量
```
//1.初始化一个变量
var i = 1;

//2.在循环中设置一个条件表达式
while(i < 10){

  //3.定义一个更新表达式，每次更新初始化变量
  document.write(i++ +"<br/>");
}
```
### 22.3.2 do...while循环
- 语法：
```
do{
  语句...
}while(条件表达式)
```
- 执行流程
  - `do...while`语句在执行时，会先执行循环体
  - 循环体执行完毕后，再对`while`后的表达式进行判断
  - 如果结果为`true`，则继续执行循环体，执行完毕继续判断依次类推
  - 如果结果为`false`，则终止循环
```
var i = 1;

do{
  document.write(i++ +"<br/>");
}while(i <= 10)
```
- `while`循环和`do...while`循环的区别
  - 实际上`while`循环和`do...while`循环功能类似，不同的是`while`是先判断后执行，而`do...while`是先执行后判断
  - `do...while`可以保证循环体至少执行一次，而`while`不能
### 22.3.3 for循环
- 在for循环中，为我们提供了专门的位置用来放三个表达式：
  - 初始化表达式
  - 条件表达式
  - 更新表达式 
- 语法：
```
for(①初始化表达式;②条件表达式;④更新表达式){
  ③语句...
}
```
- 执行流程
  - ①执行初始化表达式，初始化变量(初始化表达式只会执行一次)
  - ②执行条件表达式，判断是否执行循环
    - 如果为`true`，则执行循环语句③
    - 如果为`false`，终止循环
  - ④执行更新表达式，更新表达式执行完毕继续重复②
- `for`循环中的三个部分都可以省略，也可以写在外部
  - 如果在`for`循环中不写任何的表达式，只写两个`;`
  - 此时循环是一个死循环会一直执行下去，慎用 <br/>

例子1:
```
//打印1-100之间所有奇数之和
<script>
    var sum = 0; 
    for(var i = 0; i <= 100; i++){
      if(i%2 !== 0){
        sum += i;
      }
    }
    alert("奇数之和为：" + sum);
</script>
```
例子2:
```
<script>
    //打印1-100之间所有7的倍数的个数及总和
    var sum = 0;
    var count = 0;
    for (var i = 1; i <= 100; i++) {
      if (i % 7 == 0) {
        sum += i;
        //7倍数的个数
        count++;
      }
    }
    alert("1-100之间所有7的倍数的个数为：" + count + "，总和为：" + sum);
</script>
```
例子3:
```
<script>
    // 水仙花是指一个3位数，他的每个位数上的数字的3次幂之和等于它本身。
    //例如：1^3 + 5^3 + 3^3 = 153
    
    for (var i = 100; i <= 999; i++) {
      
      //获取百位数字
      var bai = parseInt(i / 100);
      //获取十位数字
      var shi = parseInt((i % 100) / 10);
      //获取个位数字
      var ge = i % 10;
      
      //判断i是否是水仙花数
      if ((Math.pow(bai, 3)) + Math.pow(shi, 3) + Math.pow(ge, 3) == i) {
        alert(i);
      }
    }
</script>
```
例子4:
```
<script>
    //在页面中接收一个用户输入的数字，并判断该数是否是质数
    //质数：只能被1和它自身整除的数，1不是质数也不是合数，质数必须是大于1的自然数
    var num = prompt("请输入一个数字：");
        
    if (num > 1 && !isNaN(num)) {
      //创建一个布尔值，用来保存结果，默认i是质数
      var flag = true;

      //判断i是否是质数
      //获取2-i之间的所有的数
      for (var i = 2;i < num;i++) {
        //判断i是否能被j整除
        if (num % i == 0) {
          //如果进入判断则证明i不是质数，修改flag值为false
          flag = false;   

          //一旦进入判断，则证明i不可能是质数了，此时循环再执行已经没有任何意义了
          //可以使用break来结束循环
          break;
        }
      }
      if(flag){
        alert(num + "：是质数");
      }else{
        alert(num + "：不是质数")
      }
    } else {
      alert("数字错误，请重新输入数字！");
    }
</script>
```
### 22.3.4 嵌套的for循环
```
<title>打印1-100之间所有的质数</title>
<script>
  var flag;
  for (var i = 2; i <= 100; i++) {
    flag = true;    
    for (var j = 2; j < i; j++) {
      if (i % j == 0) {
        flag = false;
        break;
      }
    }
    if (flag) { 
      document.write(i + " ");
    }
  }
</script>
```
### 22.3.5 break和continue
- `break`关键字可以用来退出`switch`或循环语句。`break`关键字会立即终止离它最近的那个循环语句。<br/>
```
//break结束的是内层循环
for(var i = 0; i < 5; i++){
  console.log("外层循环" + i);
  for(var j = 0; j < 5; j++){
    break;
    console.log("内层循环" + j);
  }
}
```
- 可以为循环语句创建一个`label`，来识别当前的循环。
  - `label`: 循环语句
  - 使用`break`语句时，可以在`break`后跟着一个`label`
  - 这样`break`将会结束指定的循环，而不是最近的
```
outer:
for(var i = 0; i < 5; i++){
  console.log("外层循环" + i);
  for(var j = 0; j < 5; j++){
    break outer;
    console.log("内层循环" + j);
  }
}
```
- `continue`关键字可以用来跳过当此循环
  - 同样continue也是默认只会对离它最近的循环起作用
  - 也可以使用`label`: 循环语句，这样将会跳出指定的循环，而不是最近的
- `console.time("计时器的名字")`：测试程序的性能
  - 可以用来开启一个计时器
  - 它需要一个字符串作为参数，这个字符串将会作为计时器的标识
- `console.timeEnd("计时器的名字")`
  - 用来停止一个计时器
  - 需要一个计时器的名字作为参数
```
//开启一个计时器
console.time("test");

被执行的代码

//停止一个计时器
console.timeEnd("test");
```
```
//提升练习"打印1-100之间所有的质数"的性能
<script>
    var flag;
    onsole.time("test");
    for (var i = 2; i <= 100; i++) {
      flag = true;    
      //Math.sqt():平方根
      for (var j = 2; j < Math.sqrt(i); j++) {
        if (i % j == 0) {
          flag = false;
          break;
        }
      }
      if (flag) { 
        document.write(i + " ");
      }
    }
    console.timeEnd("test");
</script>
```
## 23. 对象：Object
### 23.1 简介
#### 23.1.1 定义
- 基本数据类型
  - `String`：字符串
  - `Number`：数值
  - `Boolean`：布尔值
  - `Null`：空值
  - `Undefined`：未定义
- 引用数据类型
  - `Object`：对象 <br/>
使用基本数据类型的数据，我们所创建的变量都是独立的，不能成为一个整体。 <br/>
对象属于一个复合的数据类型，在对象中可以保存多个不同数据类型的属性。<br/>
#### 23.1.2 对象的分类
- 内建对象
  - 由ES标准中定义的对象，在任何的ES的实现中都可以使用
  - 比如：`Math` `String` `Number` `Boolean` `Function` `Object`...
- 宿主对象
  - 由JS的运行环境提供的对象，目前来将主要指由浏览器提供的对象
  - 比如：`BOM`(浏览器对象模型) `DOM`(文档对象模型)
- 自定义对象
  - 由开发人员自己创建的对象
### 23.2 对象的基本操作
- 创建对象
  - 使用`new`关键字调用的函数，是构造函数`constructor`
  - 构造函数是专门来创建对象的函数
  - 使用`typeof`检查一个对象时，会返回`object`
```
var obj = new Object();
```
- 添加属性
  - 在对象中保存的值称为属性
  - 向对象添加属性
    - 语法：`对象.属性名 = 属性值;`
  - 如果读取对象中没有的属性，不会报错而是会返回`undefined`
```
//向obj中添加一个name属性

obj.name = "齐天大圣";
```
- 修改对象的属性值
  - 语法：`对象.属性名 = 新值;`
```
//将对象的名字改为孙悟空
obj.name = "孙悟空";
```
- 删除对象的属性
  - 语法：`delete 对象.属性名;`
```
//将obj的name属性删除
delete obj.name;
```
- 属性名
  - 对象的属性名不强制要求遵守标识符的规范。 比如：`obj.var = "hello";`，但是使用时尽量按照标识符的规范。
  - 如果要使用特殊的属性名，不能采用`.`的方式来操作，需要使用另一种方式：
    - 语法：`对象["属性名"] = 属性值;`
```
//使用123这个属性名
obj["123"] = 789;

//读取时也需要采用这种方式
console.log(obj["123"]);
```
  - 使用`[]`这种形式取操作属性，更加的灵活
    - 在`[]`中可以直接传递一个变量，这样变量值是多少就会读取哪个属性
```
obj["123"] = 789;
obj["nihao"] = "你好";

var n = "nihao";
console.log(obj[n]);

实行结果：
你好
```
- 属性值
  - js对象的属性值，可以是任意的数据类型，甚至也可以是一个对象，或函数
```
var obj1 = new Object();
var obj2 = n;
```
例子：对象的属性值可以是一个对象
```
//创建一个对象obj2
var obj1 = new Object();
    obj1.name = "孙悟空";

//创建一个对象obj2
var obj2 = new Object();
    obj2.name = "猪八戒";

//将obj2设置为obj1的属性
obj1.test = obj2; 
        
console.log(obj1.test);
```
例子：对象的属性值可以是一个函数
```
var obj = new Object();
    obj.name = "孙悟空";
    obj.age = 18;
    //对象的属性值可以是一个函数
    obj.sayName = function () {
      console.log(this.name);
    }

//调用obj的sayName()方法
obj.sayName();

实行结果：
孙悟空
```
```
var obj = {
    name: "孙悟空",
    age: 18,
    //对象的属性值可以是一个函数
    sayName: function(){
      alert(this.name);
    }
}

//调用obj的sayName()方法
obj.sayName();

实行结果：
孙悟空
```
- 枚举对象中的属性
  - 使用`for...in`语句
  - `for...in`语句 对象中有几个属性，循环体就会执行几次
    - 每次执行时，会将对象中的一个属性的名字赋值给变量
  - 语法：
```
for(var 变量 in 对象){

}
```
例子1：打印一个对象的每个属性名
```
//定义一个person对象
var person = {
    name: "孙悟空",
    age: 18,
    gender: "男",
    address: "花果山"
}
//枚举对象中的属性
//将对象中的一个属性的名字赋值给变量n
for(var n in person){
    //打印n的属性名
    console.log("属性名：" + n);
}

实行结果：
name
age
gender
address
```
例子2：打印一个对象的每个属性名
```
//定义一个person对象
var person = {
    name: "孙悟空",
    age: 18,
    gender: "男",
    address: "花果山"
}
//枚举对象中的属性
//将对象中的一个属性的名字赋值给变量n
for(var n in person){
    //打印n的属性值
    console.log("属性值：" + person[n]);
}

实行结果：
孙悟空
18
男
花果山
```
- `in` 运算符
  - 通过该运算符可以检查一个对象中是否含有指定的属性
  - 如果有则返回`true`，没有则返回`false`
  - 语法：`"属性名" in 对象`
```
//检查obj中是否含有test2属性
console.log("test2" in obj);

实行结果：
false
```
### 23.3 基本数据类型和引用数据类型的区别
- 基本数据类型
  - `String`
  - `Number`
  - `Boolean`
  - `Null`
  - `Undefined`
- 引用数据类型
  - `Object`
- 区别1:
  - js中的变量都是保存到栈内存中的
    - 基本数据类型的值直接在栈内存中存储
    - 值与值之间是独立存在的，修改一个变量不会影响其他的变量
```
var a = 123;
var b = a;
a++;

console.log("a = " + a + ", b = " + b);

实行结果：
a = 124;
b = 123;
```
- 区别2:
  - 对象是保存到堆内存中的，每创建一个新的对象，就会在堆内存中开辟出一个新的空间
  - 而变量保存的是对象的内存地址(对象的引用)，如果两个变量保存的是同一个对象引用，
  - 当一个变量通过一个变量修改属性时，另一个也会受到影响
```
var obj = new Object();
obj.name = "孙悟空";
var obj2 = obj;
obj.name = "猪八戒";

console.log(obj2.name);

实行结果：
猪八戒  
```
```
var obj = new Object();
obj.name = "孙悟空";
var obj2 = obj;
obj2 = null;

console.log(obj2.name);

实行结果：
猪八戒  
``` 
- 区别3:
  - 当比较两个基本数据类型的值时，就是比较值。
    - 而比较两个引用数据类型时，它比较的是对象的内存地址
    - 如果两个对象是一模一样的，但是地址不同，它会返回`false`
```
<script>
  var a = 10;
  var b = 10;
  console.log(a == b); //true

  var obj1 = new Object();
  var obj2 = new Object();
  console.log(obj1 == obj2); //false
</script>
```
### 23.4 对象字面量
使用对象字面量来创建一个对象。<br/>
```
var obj = {};
obj.name = "孙悟空";

console.log(obj.name);

实行结果：
孙悟空
```
- 可以使用对象字面量，可以在创建对象时，直接指定对象中的属性
- 语法：`{属性名:属性值,属性名:属性值....}`
  - 对象字面量的属性名可以加引号也可以不加，建议不加
  - 如果要使用一些特殊的名字，则必须加引号
```
<script>
  var obj = { 
      name: "猪八戒", 
      age: 18, 
      gender: "男",
      test:{
        name: "沙和尚"
      }
  };
  console.log(obj);
</script>
```
### 23.5 `Date`对象
在js中使用`Date`对象来表示一个时间。 <br/>
- 创建一个`Date`对象
- 如果直接使用构造函数创建一个`Date`对象，则会封装为当前代码执行的时间
```     
var day = new Date();
console.log(day);

实行结果：
Wed Nov 11 2020 20:19:25 GMT+0900 (日本标准时间)
```
- 创建一个指定的时间对象
- 需要在构造函数中传递一个表示时间的字符串作为参数
- 日期的格式：月份/日/年 时:分:秒
```
var day = new Date("11/11/2020 21:01:10");
console.log(day);

实行结果：
Wed Nov 11 2020 21:01:10 GMT+0900 (日本标准时间)
```
- `getDate()`：获取当前日期对象是几日
- `getDay()`
  - 获取当前日期对象是周几
  - 会返回一个`0-6`的值
    - `0` 表示周日
    - `1` 表示周一
- `getMonth()`
  - 获取当前日期对象是几月
  - 会返回一个`0-11`的值
    - `0` 表示一月
    - `1` 表示二月
- `getFullYear()`：获取当前日期对象的年份
- `getTime()`
  - 获取当前日期对象的时间戳
  - 时间戳，指的是从格林威治标准时间的1970年1月1日0时0分0秒到当前日期所花费的毫秒数
  - 计算机底层在保存时间时使用的都是时间戳
```
var time = day.getTime();
console.log(time/1000/60/60/24/365);
```
```
//时差原因
var day = new Date("1/1/1970 0:0:0");
time = day.getTime();
console.log(time);

实行结果：
-32400000
```
- 获取当前的时间戳
```
var time = Date.now();
```
-可以利用时间戳来测试代码执行的性能
```
var start = Date.now();

for (var i = 0; i < 100; i++) {
    console.log(i);
}
var end = Date.now();
console.log("执行了：" + (end - start) + "毫秒");

实行结果：
执行了：3毫秒
```
### 23.6 `Math`对象
`Math`和其他的对象不同，它不是一个构造函数。<br/>
它属于一个工具类不用创建对象，它里面封装了数学运算相关的属性和方法。<br/>
- `Math.ceil()` 
  - 可以对一个数进行向上取整，小数位只要有值就自动进1
```
console.log(Math.ceil(1.4));

实行结果：
2
```
- `Math.floor()` 
  - 可以对一个数进行向下取整，小数部分会被舍掉
```
console.log(Math.floor(1.9));

实行结果：
1
```
- `Math.round()` 
  - 可以对一个数进行四舍五入取整 
```
console.log(Math.round(1.9));

实行结果：
2
```
- `Math.random()` 
  - 可以用来生产一个`0-1`之间的随机数
  - 也可以生成一个`0-x`之间的随机数：`Math.round(Math.random()*x)` 
```
console.log(Math.random());

实行结果：
0.3017309711879488
```
```
//可以生成一个0-10的随机数
for(var i = 0;i <10;i++){
  console.log(Math.round(Math.random()*10));
}
```
```
//生成一个1-10的随机数
console.log(Math.round(Math.random()*9)+1);
```
- 生成一个`x-y`之间的随机数
```
Math.round(Math.random()*(y-x))+x;
```
- `Math.max()`
  - 可以获取多个数中的最大值
```
var max = Maah.max(10,8,4,6,2);
console.log(max);

实行结果：
10
```
- `Math.max()`
  - 可以获取多个数中的最小值
```
var min = Maah.min(10,8,4,6,2);
console.log(min);

实行结果：
2
```
- `Math.pow(x,y)`
  - 返回`x`的`y`次幂
```
console.log(Math.pow(12,3));

实行结果：
1728
``` 
- `Math.sqrt()`
  - 用于对一个数进行开方运算
```
console.log(Math.sqrt(9);

实行结果：
3
``` 
## 24. 函数 
### 24.1 简介
- 函数也是一个对象
- 函数中可以封装一些功能(代码)，在需要时可以执行这些功能(代码)
- 函数中可以保存一些代码在需要的时候调用
- 创建一个函数对象
```
var fun = new Function();
console.log(typeof fun); //function
```
- 可以将要封装的代码以字符串的形式传递给构造函数
- 封装到函数中的代码不会立即执行
```
var fun = new Function("console.lo('Hello这是我的第一个函数');");

实行结果：
无结果
```
- 函数中的代码会在函数调用的时候执行
- 调用函数语法：`函数对象()`
- 当调用函数时，函数中封装的代码会按照顺序执行
```
var fun = new Function("console.log('Hello这是我的第一个函数');");
fun();

实行结果：
Hello这是我的第一个函数
```
- 在开发中很少使用构造函数来创建一个函数对象
### 24.2 函数声明
#### 24.2.1 使用函数声明来创建函数
- 语法：
```
function 函数名([形参1,形参2...形参N]){
  语句...
} 
```
例子：
```
function fun2(){
  console.log("这是我的第二个函数");
}
fun2();

实行结果：
这是我的第二个函数
```
#### 24.2.2 使用函数表达式来创建函数
- 语法：
```
var 函数名 = function([形参1,形参2...形参N]){
  语句...
} 
```
例子：
```
var fun3 = function(){
    console.log("我是匿名函数中封装的代码");
}
fun3();

实行结果：
我是匿名函数中封装的代码
```
### 24.3 函数的参数
定义一个用来求两个数和的函数 <br/>
- 可以在函数`()`中来指定一个或多个形参(形式函数)
- 多个形参之间使用`,`隔开，声明形参就相当于在函数内部声明了对应的变量
- 但是并不赋值
```
function sum(a, b) {
  console.log(a + b);
}
//在调用函数时，可以在`()`中指定实参(实际参数)
//实参将会赋值给函数中对应的形参
sum(1, 2);
```
- 调用函数时，解析器不会检查实参的类型
  - 所以要注意，是否有可能会接收到非法的参数，如果有可能则需要对参数进行类型的检查
- 调用函数时，解析器也不会检查实参的数量
  - 多余的实参不会被赋值
  - 如果实参的数量少于形参的数量，则没有对应实参的形参将是`undefined`
  - 函数的实参可以是任意的数据类型
### 24.4 函数的返回值
创建一个函数，用来计算三个数的和。<br/>
- 可以使用`return`来设置函数的返回值
- 语法：`return 值`
```
function sum(a, b, c){
  var d = a + b + c
  return d;
}
```
- `return`后的值将会作为函数的执行结果返回
- 可以定义一个变量来接收该结果
```
function sum(a, b, c){
  var d = a + b + c
  return d;
}

//调用函数
//变量result的值就是函数的执行结果
//函数返回什么result的值就是什么
var result = sum(1, 2, 3);

console.log("result = " + result);

实行结果：
result = 6
```
- 如果`return`语句后不跟任何值就相当于返回一个`undefined`
- 如果函数中不写`return`，则也会返回`undefined`
```
function sum(a, b, c){
  var d = a + b + c;
}

var result = sum(1, 2, 3);
console.log("result = " + result);

实行结果：
result = undefined
```
- `return`后可以跟任意类型的值，包括对象，函数
```
function fun(){
  var obj = {
      name: "沙和尚"
  }
  return obj;
}
var a = fun();
console.log("a = " + a.name);

实行结果：
a = 沙和尚
```
- `return`可以结束整个函数
```
function fun() {
  console.log("函数要执行了");
  for (var i = 0; i < 5; i++) {
    if (i == 2) {
      //使用break可以退出当前的循环
      // break;

      // continue用于跳过当次循环
      // continue;

      //return可以结束整个函数
      return;
    }
    console.log("i = " + i);
  }
  console.log("函数执行完了");
}

//调用fun()函数
fun();
```
### 24.5 立即执行函数
- 函数定义完，立即被调用，这种函数就叫做立即执行函数
- 立即执行函数往往只会执行一次  <br/>

例子1：
```
(function(){
  alert("我是一个匿名函数");
})();
```
例子2：
```
(function(a,b){
  console.log("a = " + a);
  console.log("b = " + b);
  console.log("a + b = " + (a + b));
})(123,456);

实行结果：
a = 123
b = 456
a + b = 579
```
### 24.6 练习
- 练习1：定义一个函数，判断一个数字是否是偶数，如果是返回`ture`，否则返回`false`
```
function isOu(num){
  return num % 2 == 0;
}
var result = isOu(12);
console.log("result = " + result);

实行结果：
result = true
```
- 练习2：定义一个函数，可以根据半径计算一个圆的面积，并返回结果
```
function area(radius) {
  return Math.PI * Math.pow(radius, 2);
}

var result = area(3);
console.log("result = " + result);

实行结果：
result = 28.274333882308138
```
- 练习3：创建一个函数，可以在控制台中输出一个人的信息 <br/>
- 知识点1：实参可以是一个对象 
```
//实参可以是任意的数据类型，也可以是一个对象
//当我们的参数过多时，可以将参数封装到一个对象中，然后通过对象传递
//创建一个person对象
var person = {
    name: "孙悟空",
    age: 800,
    gender: "男",
    address: "花果山"
}

//接收person对象，并打印处person的信息
function personInfo(person) {
    console.log("我叫: " + person.name + "," + "我" + person.age + "岁了," + "我是" + person.gender + "的," + "我住在" + person.address);
}

//向personInfo里面传递一个person对象
personInfo(person);
```
- 知识点2：实参也可以是一个函数
```
//创建一个对象
var person = {
    name: "孙悟空",
    age: 800,
    gender: "男",
    address: "花果山"
}

//personInfo函数
function personInfo(person) {
  //打印person的具体信息
  console.log("我叫: " + person.name + "," + "我" + person.age + "岁了," + "我是" + person.gender + "的," + "我住在" + person.address);
}

//形参info接收personInfo函数这个实参
function fun(info){
  //给personInfo函数传递一个person的对象
  info(person);
}

//调用personInfo函数
fun(personInfo);
```
### 24.7 函数的方法
#### 24.7.1 `call()`和`apply()`
- 这两种方法都是函数对象的方法，需要通过函数对象来调用
- 当对函数调用`call()`和`apply()`都会调用函数执行
```
function fun(){
  alert("我是fun函数");
}

//以下三行代码，都可以调用fun()函数
fun();
fun.call();
fun.apply();
```
- 不同的是：在调用`call()`和`apply()`可以将一个对象指定为第一个参数
  - 此时，这个对象将会成为函数执行时的`this` <br/>

例子1:
```
function fun(){
  alert(this);
}

var obj = {};

fun(); //[object Window]
fun.call(obj); //[object Object]
fun.apply(obj); //[object Object]
```
例子2：
```
function fun() {
  alert(this);
}

var obj1 = { name: "孙悟空" };
var obj2 = { name: "猪八戒" }

fun(); //[object Window]
fun.call(obj1.name); //孙悟空
fun.apply(obj2.name); //猪八戒
```
例子3: 参数是谁，this就是谁
```
var obj1 = {
    name: "孙悟空",
    sayName: function () {
      alert(this.name);
    }
};
var obj2 = { name: "猪八戒" }
obj1.sayName(); //孙悟空
obj1.sayName.apply(obj2);//猪八戒
```
- `call()`方法可以将实参在对象之后依次传递
```
function fun(a, b) {
  console.log("a = " + a);
  console.log("b = " + b);
}

var obj1 = {
  name: "孙悟空",
  sayName: function () {
    alert(this.name);
  }
};

fun.call(obj1,2,3);

实行函数：
a = 2
b = 3
```
- `apply()`方法需要将实参封装到一个数组中统一传递，而不能像`call()`方法那样将实参依次传递
```
function fun(a, b) {
  console.log("a = " + a);
  console.log("b = " + b);
}

var obj1 = {
  name: "孙悟空",
  sayName: function () {
    alert(this.name);
  }
};

fun.call(obj1,[2,3]);

实行函数：
a = 2
b = 3
```
- 总结：`this`的情况
  - 以函数形式调用时，`this`永远是`window`
  - 以方法形式调用时，`this`是调用方法的对象
  - 以构造函数的形式调用时，`this`是新创建的那个对象
  - 使用`call()`和`apply()`调用时，`this`是指定的那个对象
### 24.8 `arguments`
- 在调用函数时，浏览器每次都会传递两个隐含的参数：
  - 函数的上下文对象：`this`
  - 封装实参的对象：`arguments`
- `arguments`是一个类数组对象，它可以通过索引来操作数组，也可以获取长度
- 在调用函数时，我们所传递的实参都会在`arguments`中保存
- `arguments.length`可以用来获取实参的长度
```
function fun(){
  //输出实参的长度
  alert(arguments.length);
  alert(arguments[0]);
}

//2个实参
fun("Hello","World");

实行结果：
2
Hello
```
- 综合以上所述，可以得出即使不定义形参，也可以通过`arguments`来使用实参
  - `arguments[0]` 表示第一个实参
  - `arguments[1]` 表示第二个实参
- `arguments`里面有一个属性叫做`callee`
- 这个属性对应一个函数对象，就是当前正在指向的函数的对象
```
function fun(){
  console.log(arguments.length);
  console.log(arguments.callee);
}
fun("Hello","World");

实行结果：
fun(){
  console.log(arguments.length);
  console.log(arguments.callee);
}
```
## 25. 作用域：Scope
作用域指一个变量的作用的范围 <br/>
在js中一共有两种作用域： 全局作用域，函数作用域
### 25.1 全局作用域
- 直接编写在`script`标签中的js代码，都在全局作用域
- 全局作用域在页面打开时创建，在页面关闭时销毁
- 在全局作用域中，有一个全局对象`window`，可以直接使用。
  - 它代表的是一个浏览器的窗口，它由浏览器创建我们可以直接使用
- 在全局作用域中：
  - 创建的变量都会作为`window`对象的属性保存
  - 创建的函数都会作为`window`对象的方法保存
```
//创建的变量都会作为window对象的属性保存 
<script>

  var a = 10;
  var b = 20;

  console.log(window.b); //和console.log(b);一样
</script>

实行结果：
20
```
```
//创建的变量都会作为window对象的属性保存 
<script>

  function fun(){
    console.log("我是fun函数");
  }

  window.fun(); //和fun();一样

</script>

实行结果：
我是fun函数
```
- 变量的声明提前
  - 使用`var`关键字声明的变量，会在所有的代码执行之前被声明(但是不会赋值)
  - 但是如果声明变量时不使用`var`关键字，则变量不会被声明提前
```
console.log("a = " + a);

var a = 123;

实行结果：
a = undefined
```
以上代码相当于以下代码
```
var a;
console.log("a = " + a);

a = 123;

实行结果：
a = undefined
```
```
console.log("a = " + a);

a = 123;

实行结果：报错
Uncaught ReferenceError: a is not defined
```
- 函数的声明提前
  - 使用函数声明形式创建的函数`function 函数名(){}`
    - 它会在所有的代码执行之前就被创建，所以我们可以在函数声明前来调用函数
  - 使用函数表达式创建的函数`var fun = function(){}`
    - 不会被声明提前，所以不能在声明前调用
```
//函数声明会被提前创建
fun1();
function fun1(){
  console.log("我是一个fun1函数");
}

实行结果：
我是一个fun1函数
```
```
//函数表达式不会被提前创建
fun2();
var fun2 = function(){
  console.log("我是一个fun2函数");
}

实行结果：报错
Uncaught TypeError: fun2 is not a function
```
- 全局作用域中的变量都是全局变量，在页面的任意部分都可以访问的到
### 25.2 函数作用域
- 调用函数时创建函数作用域，函数执行完毕之后，函数作用域销毁。
- 每调用一次函数就会创建一个新的函数作用域，他们之间是相互独立的。
- 在函数作用域中可以访问到全局作用域的变量。
- 在全局作用域中无法访问到函数作用域的变量。
- 当在函数作用域中操作一个变量时，它会先在自身的作用域中寻找
  - 如果有，就直接使用
  - 如果没有，则向上一级作用域中寻找，直到找到全局作用域
  - 如果全局作用域中依然没有找到，则会报错`ReferenceError`
- 在函数中要访问全局变量可以使用`window`对象
```
function fun() {
  //函数作用域的变量
  var a = 20;
}
fun();
console.log("a = " + a);

实行结果：报错
Uncaught ReferenceError: a is not defined
```
- 在函数作用域中也有声明提前的特性
  - 使用`var`关键字声明的变量，会在函数中所有的代码执行之前被声明
  - 函数声明也会在函数中所有的代码执行之前执行 <br/>

例子1: 
```
function fun(){
  console.log(a);
  var a = 35;
}
fun();

实行结果：
undefined
```
例子2:
```
function fun1(){
  
  fun2();

  function fun2(){
    alert("I'm fun2");
  }

}
fun1();

实行结果： 
I'm fun2
```
例子3:
```
var a = 33;

function fun(){
  console.log("a = " + a);
  var a = 10;
}

fun();

实行结果：
a = undefined
```
例子4:
```
var a = 33;

function fun(){
  console.log("a = " + a);
  a = 10;
}

fun();

实行结果：
a = 33
```
- 在函数中，不使用`var`声明的变量都会成为全局变量
```
var a = 33;
function fun(){
  a = 10;
}
fun();
        
//在全局中输出a
console.log("a = " + a);

实行结果：
a = 10
```
- 定义形参就相当于在函数作用域中声明了变量
```
var a = 33;

//定义形参就相当于在函数作用域中声明了变量
function fun(a){ //相当于在fun()函数中声明了 var a;
  alert(a);
}
fun();

实行结果：
undefined
```
### 25.3 练习
练习1:
```
var a = 123;
function fun(){
  alert(a);
}
fun();

实行结果：
123
```
练习2:
```
var a = 123;
function fun(){
  alert(a);
  var a = 456;
}
fun();
alert(a);

实行结果：
undefined
123
```
练习4:
```
var a = 123;
function fun(a){
  alert(a);
  a = 456;
}
fun();
alert(a);

实行结果：
undefined
123 
```
练习5:
```
var a = 123;
function fun(a){
  alert(a);
  a = 456;
}
fun(123);
alert(a);

实行结果：
123
123 
```
### 25.4 this
解析器在调用函数时，每次都会向函数内部传递进一个隐含的参数。这个隐含的参数就是`this`。<br/>
- `this`指向的是一个对象，这个对象我们称为函数执行的上下文对象。
- 根据函数的调用方式的不同，`this`会指向不同的对象
  - 以函数的形式调用时，`this`永远都是`window`
  - 以方法的形式调用时，`this`就是调用方法的那个对象

例子1:
```
function fun(){
  console.log(this);
}
//创建一个对象
var obj = {
    name: "孙悟空",
    sayName:fun
}
//以函数的形式调用时，this永远都是window
fun();

实行结果：
object Window
```
例子2:
```
function fun(){
  console.log(this);
}
//创建一个对象
var obj = {
    name: "孙悟空",
    sayName:fun
}

//以方法的形式调用时，this就是调用方法的那个对象
obj.sayName();

实行结果：
//object Object
name: 孙悟空
sayName: fun()
```
例子3:
```
var name = "全局的name属性";

function fun(){
  console.log(this.name);
}

//创建一个对象
var obj = {
    name: "孙悟空",
    sayName:fun
}

fun();

实行结果：
全局的name属性
```
例子4:
```
var name = "全局的name属性";

function fun(){
  console.log(this.name);
}

//创建一个对象
var obj = {
    name: "孙悟空",
    sayName:fun
}

obj.sayName();

实行结果：
孙悟空
```
## 26. 使用工厂方法创建对象
通过该方法可以大批量的创建对象。
```
function createPerson(name,age,gender){
  //创建一个新的对象 
  var obj = new Object();

  //向对象中添加属性
  obj.name = name;
  obj.age = age;
  obj.gender = gender;
  obj.sayName = function(){
      console.log(this.name);
  }

  //将新的对象返回
  return obj;
}
        
var obj1 = createPerson("孙悟空",18,"男");
var obj2 = createPerson("猪八戒",28,"男");
var obj3 = createPerson("沙和尚",38,"男");

console.log(obj1);
console.log(obj2);
console.log(obj3);
        
obj1.sayName();
obj2.sayName();
obj3.sayName();

实行结果：
{name: "孙悟空", age: 18, gender: "男", sayName: ƒ}
{name: "猪八戒", age: 28, gender: "男", sayName: ƒ}
{name: "沙和尚", age: 38, gender: "男", sayName: ƒ}
孙悟空
猪八戒
沙和尚
```
## 27. 构造函数
### 27.1 定义
构造函数就是一个普通的函数，创建方式和普通函数没有区别，<br/>
不同的是构造函数习惯上首字母大写。<br/>
- 构造函数和普通函数的区别就是调用方式的不同
  - 普通函数是直接调用，而构造函数需要使用`new`关键字来调用
```
function Person(){

}  
var per = new Person();
```
### 27.2 执行流程
- 立刻创建一个新的对象
- 将新建的对象设置为函数中的`this`，在构造函数中可以使用`this`来引用新建的对象
- 逐行执行函数中的代码
- 将新建的对象作为返回值返回
### 27.3 类
使用一个构造函数创建的对象，我们称为一类对象，也将一个构造函数称为一个类 <br/>
我们将通过一个构造函数创建的对象，称为是该类的实例
```
//创建一个构造函数，也称为创建一个Person类
function Person(name,age,gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = function(){
        alert(this.name);
    }
}
//Person类的实例    
var per1 = new Person("孙悟空",18,"男");
var per2 = new Person("猪八戒",28,"男");
var per3 = new Person("沙和尚",38,"男");

//在控制台输出三个Person类的实例
console.log(per1);
console.log(per2);
console.log(per3);

实行结果：
Person {name: "孙悟空", age: 18, gender: "男", sayName: ƒ}
Person {name: "猪八戒", age: 28, gender: "男", sayName: ƒ}
Person {name: "沙和尚", age: 38, gender: "男", sayName: ƒ}
```
### 27.4 `instanceof`
- `instanceof`可以检查一个对象是否是一个类的实例
  - 语法：`对象 instanceof 构造函数`
  - 如果是，则返回`true`，否则返回`false`
```
console.log(per instanceof Person);

实行结果：
true
```
- 所有的对象都是`Object`的后代
  - 所有任何对象和`Object`做`instanceof`检查时都会返回`true`
### 27.4 `this`总结：
  - 当以函数的形式调用时，`this`是`window`
  - 当以方法的形式调用时，谁调用方法`this`就是谁
  - 当以构造函数的形式调用时，`this`就是新创建的那个对象
### 27.4 构造函数修改
在`Person`构造函数中，为每一个对象都添加了一个`sayName`方法，<br/>
之前我们的方法是在构造函数内部创建的，也就是构造函数每执行一次就会创建一个新的`sayName`方法，<br/>
也就是所有实例的`sayName`都是唯一的，这样就导致了构造函数执行一次就会创建一个新的方法，<br/>
执行10000次就会创建10000个新的方法，而10000个方法都是一模一样的，<br/>
这是完全没有必要，完全可以使所有的对象共享同一个方法。<br/>
可以将`sayName`方法在全局作用域中定义。<br/>

修改前：
```
//创建一个构造函数，也称为创建一个Person类
function Person(name,age,gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = function(){
        alert("大家好，我是" + this.name);
    }
}
//Person类的实例    
var per1 = new Person("孙悟空",18,"男");
var per2 = new Person("猪八戒",28,"男");
var per3 = new Person("沙和尚",38,"男");

per1.sayName();
console.log(per1.sayName == per2.sayName);

//在控制台输出三个Person类的实例
console.log(per1);
console.log(per2);
console.log(per3);

实行结果：
大家好，我是孙悟空
false
Person {name: "孙悟空", age: 18, gender: "男", sayName: ƒ}
Person {name: "猪八戒", age: 28, gender: "男", sayName: ƒ}
Person {name: "沙和尚", age: 38, gender: "男", sayName: ƒ}
```
修改后：
```
//创建一个构造函数，也称为创建一个Person类
function Person(name,age,gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = sayName; 
}

//将sayName方法在全局作用域中定义
function sayName(){
    alert("大家好，我是" + this.name);
}

//Person类的实例    
var per1 = new Person("孙悟空",18,"男");
var per2 = new Person("猪八戒",28,"男");
var per3 = new Person("沙和尚",38,"男");

per1.sayName();
console.log(per1.sayName == per2.sayName);

//在控制台输出三个Person类的实例
console.log(per1);
console.log(per2);
console.log(per3);

实行结果：
大家好，我是孙悟空
true
Person {name: "孙悟空", age: 18, gender: "男", sayName: ƒ}
Person {name: "猪八戒", age: 28, gender: "男", sayName: ƒ}
Person {name: "沙和尚", age: 38, gender: "男", sayName: ƒ}
```
## 28. 原型对象: prototype
问题：以下代码，将函数定义在全局作用域，污染了全局作用域的命名空间。<br/>
而且定义在全局作用域中也很不安全。
```
//将sayName方法在全局作用域中定义
function sayName(){
    alert("大家好，我是" + this.name);
}
```
- 我们所创建的每一个函数，解析器都会向函数中添加一个属性`prototype`。
  - 这个属性对应着一个对象，这个对象就是我们所谓的原型对象。
- 如果函数作为普通函数调用`prototype`没有任何作用
- 当函数以构造函数的形式调用时，它所创建的对象中都有一个隐含的属性，
  - 指向该构造函数的原型对象，我们可以通过`__proto__`来访问属性
```
function Myclass() {

}
var mc1 = new Myclass();
var mc2 = new Myclass();
        
console.log(mc1.__proto__ == Myclass.prototype);

实行结果：
true
```
- 原型对象就相当于一个公共区域，它会先在对象自身中寻找，如果有则直接使用。
- 如果没有则会去原型对象中寻找，如果找到则直接使用。
```
function Myclass() {

}

Myclass.prototype.a = 123;

var mc1 = new Myclass();
var mc2 = new Myclass();
        
//向mc中添加a属性
mc1.a = "我是mc1中的a属性"
console.log(mc1.a);

实行结果：
我是mc1中的a属性
```
```
function Myclass() {

}

Myclass.prototype.a = 123;

var mc1 = new Myclass();
var mc2 = new Myclass();
        
console.log(mc1.a);

实行结果：
123
```
```
function Person(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
}

//向Person的原型中添加一个方法
Person.prototype.sayName = function () {
    alert("大家好，我是" + this.name);
}

var per1 = new Person("孙悟空", 18, "男");
var per2 = new Person("猪八戒", 28, "男");
var per3 = new Person("沙和尚", 38, "男");

per1.sayName();

实行结果：
大家好，我是孙悟空
```
- 以后我们创建构造函数时，可以将这些对象共有的属性和方法，统一添加到构造函数的原型对象中
- 这样不用分别为每一个对象添加，也不会影响到全局作用域，就可以使每个对象都具有这些属性和方法了
- 使用`in`检查对象中是否含有某个属性时，如果对象中没有但是原型中有，也会返回`true`
```
function MyClass(){

}

//向MyClass的原型中添加一个name属性
MyClass.prototype.name = "我是原型中的名字";

var mc = new MyClass();

console.log("name" in mc);

实行结果：
true
```
- 可以使用对象中的`hasOwnProperty()`来检查对象自身中是否含有该属性
- 使用该方法只有当对象自身中含有属性时，才会返回`true`
```
console.log(mc.hasOwnProperty("name"));

实行结果：
false
```
- 原型对象也是对象，所以它也有原型
  - 当我们使用一个对象的属性或方法时，就先在自身中寻找
    - 自身中如果有，则直接使用
    - 如果没有则去原型对象中寻找，如果原型对象中有，则使用
    - 如果没有则去原型的原型中寻找，直到找到`Object`对象的原型
    - `Object`对象的原型没有原型，如果在`Object`中依然没有找到，则返回`undefined`
```
console.log(mc.__proto__.proto__.hasOwnProperty("hasOwnProperty"));

实行结果：
true
```
## 29. `toString()`
当我们直接在页面中打印一个对象时，实际上是输出的对象的`toString()`方法的返回值
```
function Person(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
}

//创建一个Person的实例
var per = new Person("孙悟空", 18, "男");

//以下代码相当于console.log(per);
var result = per.toString();
console.log("result = " + result);

实行结果：
result = [object Object]
```
- 如果我们希望在输出对象时不输出`[object Object]`，可以为对象添加一个`toString()`方法
```
function Person(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
}

//创建Person的实例
var per1 = new Person("孙悟空", 18, "男");
var per2 = new Person("猪八戒", 28, "男");

//添加toString方法
per1.toString = function(){
    return "Person[name="+this.name+",age="+this.name+",gender="+this.gender+"]";
}

console.log(per1);

实行结果：
Person {name: "孙悟空", age: 18, gender: "男", toString: ƒ}
```
- 以上代码如果换成输出`per2`，则必须再次修改`toString`，将`per1.toString()`改为`per2.toString()`
  - 为了避免以上这种情况，我们可以修改`Person`原型的`toString`
```
function Person(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
}

//创建Person的实例
var per1 = new Person("孙悟空", 18, "男");
var per2 = new Person("猪八戒", 28, "男");

//修改Person原型的toString
Person.prototype.toString = function(){
  return "Person[name="+this.name+",age="+this.name+",gender="+this.gender+"]";
}
console.log(per1);
console.log(per2);

实行结果：
Person {name: "孙悟空", age: 18, gender: "男"}
Person {name: "猪八戒", age: 28, gender: "男"}
```
## 30. 垃圾回收：GC
程序运行过程中会产生垃圾，垃圾积攒过多后，会导致程序运行的速度过慢，<br/>
所以我们需要一个垃圾回收的机制，来处理程序运行过程中产生的垃圾。<br/>
- 当一个对象没有任何的变量或属性对它进行引用，此时我们将永远无法操作该对象，
- 此时这样对象就是一个垃圾，这种对象过多会占用大量的内存空间，导致程序运行变慢
- 所以这种垃圾必须清理。
- 在js中拥有自动的垃圾回收机制，会自动将这种垃圾对象从内存中销毁
- 我们不需要也不能进行垃圾回收操作
- 我们需要做的只是要将不再使用的对象设置为`null`即可
```
var obj = new Object();

//不再使用此对象
obj = null;
```
## 31. 数组 `Array`
### 31.1 简介
#### 31.1.1 定义
- 数组也是一个对象
- 它和普通对象类似，也是用来存储一些值的
- 不同的是普通对象是使用字符串作为属性名的，而数组是使用数字作为索引操作元素
  - 索引：从0开始的整数
- 数组的存储性能比普通对象好，在开发中我们经常使用数组来存储一些数据
#### 31.1.2 流程
- 创建对象
```
//创建数组对象
var arr = new Array();

//使用typeof检查一个数组时，会返回object
console.log(typeof arr);

实行结果：
object 
```
- 向数组中添加元素
  - 语法：`数组[索引] = 值;`
```
//创建数组对象
var arr = new Array();

//向数组中添加元素
arr[0] = 10;
arr[1] = 33;
arr[2] = 22;

console.log(arr);

实行结果：
[10, 33, 22]
```
- 读取数组中的元素
  - 语法：`数组[索引]`
  - 如果读取不存在的索引，不会报错而是会返回`undefined`
```
//创建数组对象
var arr = new Array();

//向数组中添加元素
arr[0] = 10;
arr[1] = 33;
arr[2] = 22;

//读取数组中的元素
console.log(arr[0]);

实行结果：
10
```
- 获取数组的长度
  - 可以使用`length`属性来获取数组的长度(元素的个数)
  - 语法： `数组.length`
  - 对于连续的数组，使用`length`可以获取到数组的长度(元素的个数)
  - 对于非连续的数组，使用`length`会获取到`数组的最大的索引+1`
```
//创建数组对象
var arr = new Array();

//向数组中添加元素
arr[0] = 10;
arr[1] = 33;
arr[2] = 22;

//获取数组的长度
console.log(arr.length);

实行结果：
3
```
- 修改数组的长度
  - 如果修改的`length`大于原长度，则多出部分会空出来
  - 如果修改的`length`小于原长度，则多出元素会被删除
- 向数组的最后一个位置添加元素
  - 语法：`数组[数组.length] = 值;`
```
//创建数组对象
var arr = new Array();

arr[0] = 10;
arr[1] = 33;
arr[2] = 22;

//向数组的最后一个元素添加元素
arr[arr.length] = 11;
//向数组的最后一个元素添加元素
arr[arr.length] = 55;
//向数组的最后一个元素添加元素
arr[arr.length] = 66;

console.log(arr);

实行结果：
[10, 33, 22, 11, 55, 66]
```
### 31.2 数组字面量
- 使用字面量来创建数组。<br/>
- 语法：`[]`
```
var arr = [];

console.log(typeof arr);

实行结果：
object
```
- 使用字面量创建数组时，可以在创建时就指定数组中的元素
```
var arr = [1, 2, 3, 4, 5];
```
- 使用构造函数创建数组时，也可以同时添加元素，将要添加的元素作为构造函数的参数传递
  - 元素之间使用`,`隔开
```
var arr = new Array(10,20,30);
```
- 创建一个数组，数组中只有一个元素10
```
//创建一个数组，数组中只有一个元素，值为10
arr1 = [10];
console.log(arr1);
        
//创建一个长度为10的数组
arr2 = new Array(10);
console.log(arr2);
```
- 数组中的元素可以是任意的数据类型，也可以是对象，函数
```
//任意数据
arr = ["hello", 1, true, null, undefined];

console.log(arr[]);

实行结果：
["hello", 1, true, null, undefined]
```
```
//对象
arr = [{name:"孙悟空"},{name:"猪八戒"},{name:"沙和尚"}];
console.log(arr);

实行结果：
0: {name: "孙悟空"}
1: {name: "猪八戒"}
2: {name: "沙和尚"}
```
```
//函数
arr = [function(){alert(1)},function(){alert(2)}];
alert(arr);
arr[0]();

实行结果：
function(){alert(1)},function(){alert(2)}
1
```
- 数组中也可以放数组，如下这种数组称为二维数组
```
arr = [[1,2,3],[3,4,5],[5,6,7]];
alert(arr[0]);

实行结果：
1,2,3
```
### 31.3 数组的方法
#### 31.3.1 `push()`
- 该方法可以向数组的末尾添加一个或多个元素，并返回数组的新的长度
- 可以将要添加的元素作为方法的参数传递，这样这些元素将就自动添加到数组的末尾
- 该方法会将数组新的长度作为返回值返回
```
var arr = ["孙悟空","猪八戒","沙和尚"];
var result = arr.push("唐僧","蜘蛛精","白骨精");
alert(arr);
alert("result = " + result);

实行结果：
孙悟空,猪八戒,沙和尚,唐僧,蜘蛛精,白骨精
result = 6
```
#### 31.3.2 `pop()`
- 该方法可以删除数组中的最后一个元素，并将被删除的元素作为返回值返回
```
var arr = ["孙悟空","猪八戒","沙和尚"];
alert(arr);

//删除数组最后一个元素:沙和尚
var result = arr.pop();
alert(arr);
alert("result = " + result); //沙和尚

//删除数组最后一个元素：猪八戒
arr.pop();
alert(arr);

实行结果：
孙悟空,猪八戒,沙和尚

孙悟空,猪八戒
result = 沙和尚

孙悟空
```
#### 31.3.3 `unshift()`
- 该方法可以向数组的开头添加一个或多个元素，并返回数组的新的长度
- 向前边插入元素以后，其他的元素会依次调整
```
var arr = ["孙悟空","猪八戒","沙和尚"];
alert(arr);

result = arr.unshift("唐僧");
alert(arr);
alert("result = " + result);

实行结果：
孙悟空,猪八戒,沙和尚
唐僧,孙悟空,猪八戒,沙和尚
result = 4
```
#### 31.3.4 `shift()`
- 该方法可以删除数组中的第一个元素，并将被删除的元素作为返回值返回
```
var arr = ["孙悟空","猪八戒","沙和尚"];
alert(arr);

result = arr.shift();
alert(arr);
alert("result = " + result);

实行结果：
孙悟空,猪八戒,沙和尚
猪八戒,沙和尚
result = 孙悟空
```
#### 31.3.5 `slice()`
- 可以用来从数组中提取指定的元素
- 该方法不会改变元素数组，而是将截取到的元素封装到一个新的数组中返回
- 参数：
  - 截取开始的位置的索引，包含开始索引
  - 截取结束的位置的索引，不包含结束索引
    - 第二个参数可以省略不写，此时会截取从开始索引往后的所有元素
    - 索引可以传递一个负值，如果传递一个负值，则从后往前计算
      - `-1` 倒数第一个
      - `-2` 倒数第二个  <br/>

例子1:
```
var arr = ["孙悟空","猪八戒","沙和尚","白骨精"];

var result = arr.slice(0,2);
console.log(result);  

实行结果：
["孙悟空", "猪八戒"]
```
例子2:第二个参数可以省略不写，此时会截取从开始索引往后的所有元素
```
var arr = ["孙悟空","猪八戒","沙和尚","白骨精"];

var result = arr.slice(1);
console.log(result);

实行结果：
["猪八戒", "沙和尚", "白骨精"]
```

例子3:索引可以传递一个负值
```
var arr = ["孙悟空","猪八戒","沙和尚","白骨精"];

var result = arr.slice(1,-1);
console.log(result);

实行结果：
["猪八戒", "沙和尚"]
```
#### 31.3.6 `splice()`
- 可以用于删除数组中的指定元素
- 使用`splice()`会影响到原数组，会将指定元素从原数组中删除
  - 并将被删除的元素作为返回值返回
- 参数：
  - 第一个，表示开始位置的索引
  - 第二个，表示删除的数量
  - 第三个及以后，可以传递一些新的元素，这些元素将会自动插入到开始位置索引前边
```
var arr = ["孙悟空","猪八戒","沙和尚","白骨精"];
var result = arr.splice(2,2); 
console.log(result);

实行结果：
["沙和尚", "白骨精"]
```
```
var arr = ["孙悟空","猪八戒","沙和尚","白骨精"];
var result = arr.splice(2,2,"牛魔王","铁扇公主");

console.log(result); //["沙和尚", "白骨精"]
console.log(arr); // ["孙悟空", "猪八戒", "牛魔王", "铁扇公主"]
```
练习：
```
//创建一个数组
var arr = [1, 2, 3, 2, 2, 1, 3, 4, 2, 5];

//读取数组中的元素
for (var i = 0; i < arr.length; i++) {
    console.log(arr.length);
    
    //第一个元素和第二个，三个...元素比较
    for (var j = i + 1; j < arr.length; j++) {
        //判断第一个元素是否等于第二个元素
        if (arr[i] == arr[j]) {
          //如果第一个元素等于第二个元素，则将第二个元素删除
          arr.splice(j, 1);
          //第三个元素会变成第二个元素
          j--;
        }
    }
}
//打印数组去重之后的数组
console.log(arr);
```
#### 31.3.7 `concat()`
- 可以连接两个或多个数组，并将新的数组返回。
- 该方法不会对原数组产生影响。
```
var arr1 = ["孙悟空","猪八戒","沙和尚"];
var arr2 = ["白骨精","蜘蛛精","玉兔精"];
var arr3 = ["唐僧","观音","佛祖"];
var result = arr1.concat(arr2,arr3,"牛魔王");

alert(result);

实行结果：
孙悟空,猪八戒,沙和尚,白骨精,蜘蛛精,玉兔精,唐僧,观音,佛祖,牛魔王
```
#### 31.3.8 `join()`
- 该方法可以将数组转换为一个字符串
- 该方法不会对原数组产生影响
```
var arr = ["孙悟空","猪八戒","沙和尚"];
result = arr.join();

console.log(typeof result);

实行结果：
string
```
- 在`join()`中可以指定一个字符串作为参数，这个字符串将会成为数组中元素的连接符
  - 如果不指定连接符，则默认使用`,`作为连接符
```
var arr = ["孙悟空","猪八戒","沙和尚"];

result = arr.join("(^_^)");
alert(result);

实行结果：
孙悟空(^_^)猪八戒(^_^)沙和尚
```
#### 31.3.9 `reverse()`
- 该方法用来反转数组(前边的去后边，后边的去前边)
- 该方法会直接修改原数组
```
var arr = ["孙悟空","猪八戒","沙和尚"];

arr.reverse();
alert(arr);

实行结果：
沙和尚,猪八戒,孙悟空
```
#### 31.3.10 `sort()`
- 可以用来对数组中的元素进行排序
- 该方法会直接修改原数组
```
var arr = ["b","e","a","g","e","c"];

arr.sort();
alert(arr);

实行结果：
a,b,c,e,e,g
```
- 即使对于纯数字的数组，使用`sort()`排序时，也会按照Unicode编码来排序
- 所以对数字进行排序时，可能会得到错误的结果，比如：
```
var arr = [4,3,2,11,7,5];

arr.sort();
alert(arr);

实行结果：
11,2,3,4,5,7
```
- 我们可以自己来指定排序的规则
- 可以在`sort()`添加一个回调函数，来指定排序规则
  - 回调函数中需要定义两个形参
  - 浏览器将会分别使用数组中的元素作为实参去调用回调函数
  - 使用那个元素调用不确定，但是肯定是都是在数组中`a`一定在`b`前面
  - 浏览器会根据回调函数的返回值来决定元素的顺序
    - 如果返回一个大于0的值，则元素会交换位置
    - 如果返回一个小于0的值，则元素不会交换位置
    - 如果返回一个0，则认为两个元素相等，也不会交换位置 <br/>

例子1: 升序排列
```
var arr = [5, 4, 3, 2, 1, 6, 2, 4];

arr.sort(function (a, b) {
  if (a > b) {
    return 1;
  } else if (a < b) {
    return -1;
  } else {
    return 0;
  }
});

alert(arr);

实行结果：
1,2,3,4,5,6,7,8
```
例子2: 升序排列
```
var arr = [5, 4, 3, 2, 1, 6, 8, 7];

arr.sort(function (a, b) {
  return a - b;
});

alert(arr);

实行结果：
1,2,3,4,5,6,7,8
```
总结：<br/>
- 如果需要升序排列，则返回`a - b`
- 如果需要降序排列，则返回`b - a`

### 31.4 数组的遍历
遍历数组就是将数组中所有的元素都取出来。<br/>
```
var arr = ["孙悟空", "猪八戒", "沙和尚", "唐僧"];

for (var i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}

实行结果：
孙悟空
猪八戒
沙和尚
唐僧 
```
### 31.5 forEach
- 一般我们都是使用for循环去遍历数组，js中还为我们提供了一个方法`forEach`，用来遍历数组。<br/>
- `forEach`这个方法只支持ie8以上的浏览器。
  - 像这种函数，由我们创建但是不由我们调用的，我们称为回调函数
  - 数组中有几个元素，函数就会执行几次
  - 每次执行时，浏览器就会遍历到的元素，以实参的形式传递进来
  - 我们可以来定义形参，来读取这些内容
  - 浏览器会在回调函数中传递三个参数
    - 第一个参数，就是当前正在遍历的元素的值
    - 第二个参数，就是当前正在遍历的元素的索引
    - 第三个参数，就是当前正在遍历的数组
```
var arr = ["孙悟空", "猪八戒", "沙和尚", "唐僧", "白骨精"];
        
//forEach()方法需要一个函数作为参数
arr.forEach(function (value, index, obj) {
    console.log(value); // 孙悟空 猪八戒 沙和尚 唐僧 白骨精
    console.log(index); // 0 1 2 3 4
    console.log(obj); // 5个 ["孙悟空", "猪八戒", "沙和尚", "唐僧", "白骨精"]
});
```
## 32. 包装类
- 基本数据类型
  - `String` `Number` `Boolean` `Null` `Undefined`
- 引用数据类型
  - `Object`
在js中为我们提供了三个包装类，通过这三个包装类可以将基本数据类型的数据转换为对象。<br/>
- `String()`
  - 可以将基本数据类型的字符串转换为`String`对象
- `Number()`
  - 可以将基本数据类型的数字转换为`Number`对象
- `Boolean()`
  - 可以将基本数据类型的布尔值转换为`Boolean`对象
- 注意：我们在实际应用中不会使用基本数组类型的对象
  - 如果使用基本数据类型的对象，在做一些比较时可能会带来一些不可预期的结果
```
//创建一个，String，Number，Boolean类型的对象
var str = new String("hello");
var num = new Number(3);
var bool = new Boolean(true);

console.log(typeof str);
console.log(typeof num);
console.log(typeof bool);

实行结果：
object
object
object
```
- 方法和属性只能添加给对象，不能添加给基本数据类型
  - 当我们对一些基本数据类型的值去调用属性和方法时，
  - 浏览器会临时使用包装类将其转换为对象，然好再调用对象的属性和方法
  - 调完之后，再将其转换为基本数据类型
```
var s = 123;
//浏览器会临时使用包装类String()将基本数据类型s转换为对象，然好再调用对象的toString()方法  
s = s.toString();

console.log(s);
console.log(typeof s);

实行结果：
123
string
```
## 33. 字符串的方法
在底层字符串是以字符数组的形式保存的。<br/>
比如：`["H","e","l","l","o"]`
### 33.1 字符串属性
- `length` 获取字符串的长度
```
//创建一个字符串
var str = "Hello";

console.log(str.length);

实行结果：
5
```
### 33.2 字符串的方法
### 33.2.1 `charAt()`
可以返回字符串中指定位置的字符，根据索引获取指定的字符
```
var str = "Hello";
var result = str.charAt(0);

console.log("result = " + result);

实行结果：
result = H
```
### 33.2.2 `charCodeAt()`
获取指定位置字符的字符编码(Unicode编码)
```
var str = "Hello";
var result = str.charCodeAt(0);

console.log("result = " + result);

实行结果：
result = 72
```
### 33.2.3 `fromcharCode()`
可以根据字符编码去获取字符
```
var result = String.fromCharCode(72);
alert("result = " + result);

实行结果：
result = H
```
### 33.2.4 `concat()`
可以用来连接两个或多个字符串，作用和`+`一样
```
var str = "hello, ";

var result = str.concat("Nice ", "to ", "meet ", "you！");
alert(result);

实行结果：
hello, Nice to meet you！
```
### 33.2.5 `indexOf()`
- 该方法可以检索一个字符串是否含有指定内容
- 如果字符串中含有该内容，则会返回其第一次出现的索引
- 如果没有找到指定的内容，则返回`-1`
- 可以指定一个第二个参数，指定开始查找的位置
```
var str = "hello";
var result = str.indexOf("o");
alert(result); 

实行结果：
4
```
```
//指定第二个参数
var str = "hello world";
var result = str.indexOf("l",5);
alert(result);

实行结果：
9
```
### 33.2.6 `lastIndexOf()`
- 该方法的用法和`indexOf()`一样
- 不同的是`indexOf()`是从前往后找，而`lastIndexOf()`是从后往前找
- 也可以指定开始查找的位置
```
var str = "hello world";
var result = str.lastIndexOf("l");
        
alert(result);

实行结果：
9
```
```
var str = "hello world";

var result = str.lastIndexOf("l",3);
alert(result);

实行结果：
3
```
### 33.2.7 `silce()`
- 可以从字符串中截取指定的内容
- 不会影响原数组，而是将截取的内容返回
- 参数：
  - 第一个，开始位置的索引(包括开始位置)
  - 第二个，结束位置的索引(包括结束位置)
    - 如果省略第二个参数，则会截取到后边所有的字符
  - 也可以传递一个负数作为参数，负数的话，将会从后边计算
```
var str = "hello world";

var result = str.slice(1,3);
alert(result);

实行结果：
el
```
```
var str = "hello world";

var result = str.slice(1,-1);
alert(result);

实行结果：
ello worl
```
### 33.2.8 `substring()`
- 可以用来截取一个字符串，和`slice()`类似
- 参数：
  - 第一个，开始位置的索引(包括开始位置)
  - 第二个，结束位置的索引(包括结束位置)
    - 如果省略第二个参数，则会截取到后边所有的字符
- 和`slice()`不同的是这个方法不能接收负值作为参数
  - 如果传递了一个负值，则默认使用0
  - 而且它还会自动调整参数的位置，如果第二个参数小于第一个，则会自动交换
```
var str = "hello world";

var result = str.substring(1,0);
alert(result);

实行结果：
h
```
### 33.2.9 `substr()`
- 用来获取字符串
- 参数：
  - 第一个，用来截取开始位置的索引
  - 第二个，截取的长度
```
var str = "hello world";

var result = str.substr(1,4);
alert(result);

实行结果：
ello
```
### 33.2.10 `split()`
- 可以将数组串拆分为一个数组
- 参数：
  - 需要一个字符串作为参数，将会根据该字符串去拆分数组
- 如果传递一个空串作为参数，则会将每个字符都拆分为数组中的一个元素
```
var str = "hello, js, world";

var result = str.split(",");
alert(result[0]);
alert(typeof result);

实行结果：
hello
object
```
```
var str = "Hello js world";

var result = str.split("");
alert(result);

实行结果：
H,e,l,l,o, ,j,s, ,w,o,r,l,d
```
### 33.2.11 `toUpperCase()`
- 将一个字符串转换为大写并返回
```
var str = "Hello js world";

var result = str.toUpperCase();
alert(result);

实行结果：
HELLO JS WORLD
```
### 33.2.12 `toLowerCase()`
- 将一个字符串转换为小写写并返回
```
var str = "Hello js world";

var result = str.toUpperCase();
alert(result);

实行结果：
hello js world
```
## 34. 正则表达式
### 34.1 简介
正则表达式用于定义一些字符串的规则，计算机可以根据正则表达式，来检查一个字符串是否符合规则。<br/>
获取将字符串中符合规则的内容提取出来。<br/>
- 创建正则表达式
  - 语法：`var 变量 = new RegExp("正则表达式","匹配模式");`
  - 使用`typeof`检查正则对象，会返回`object`
- 正则表达式的方法
  - `test();`
  - 使用这个方法可以用来检查一个字符串是否符合正则表达式的规则
    - 如果符合则返回`true`，否则返回`false`
- 在构造函数中可以传递一个匹配模式作为第二个参数
  - `i` 忽略大小写 
  - `g` 全局匹配模式

例子1:
```
//创建正则表达式的对象
//这个正则表达式可以来检查一个字符串中是否含有a
var reg = new RegExp("a");
var str = "a";
        
//检查字符串是否符合正则表达式的规则
var result = reg.test(str);

//如果符合正则表达式则返回true，不符合返回false
alert(result);

实行结果：
true
```
例子2:
```
//创建正则表达式的对象
//这个正则表达式可以来检查一个字符串中是否含有a
var reg = new RegExp("A","i");
var str = "a";
        
//检查字符串是否符合正则表达式的规则
var result = reg.test(str);

//如果符合正则表达式则返回true，不符合返回false
alert(result);

实行结果：
true
```
例子3:
```
//创建正则表达式的对象
var reg = new RegExp("Ac","i");
var str = "abc";
        
//检查字符串是否符合正则表达式的规则
var result = reg.test(str);
//符合正则表达式则返回true，不符合返回false
alert(result);

实行结果：
false
```
### 34.2 语法
- 使用字面量来创建正则表达式
- 语法：`var 变量 = /正则表达式/匹配模式;`
- 使用字面量的方式创建更加简单，但是使用构造函数创建更加灵活
```
var reg = new RegExp("a","i");
alert(reg.test("Abc"));

实行结果：
true
```
以上代码可以写成如下方式：
```
var reg = /a/i;
alert(reg.test("Abc"))

实行结果：
true
```
- 使用`|`表示或者的意思
```
//创建一个正则表达式，检查一个字符串中是否含有a或b
var reg = /a|b/i;
alert(reg.test("bc"));

实行结果：
true
```
- `[]`里的内容也是或的关系 
  - `[a-z]` 任意的小写字母
  - `[A-Z]` 任意的大写字母
  - `[A-z]` 任意字母
  - `[0-9]` 任意数字
```
//检查字符串中是否含有字母
var reg = /[A-z]/;
alert(reg.test("a"));

实行结果：
true
```
```
//检查一个字符串中是否含有 abc 或 adc 或 aec
var reg = /a[bde]c/;
alert(reg.test("abc"));

实行结果：
true
```
- `[^ ]` 除了
```
var reg = /[^ab]/;
alert(reg.test("abc"));

实行结果：
true
```
### 34.3 字符串和正则相关的方法
#### 34.3.1 `split()`
- 可以将一个字符串拆分为一个数组。
- 方法中可以传递一个正则表达式作为参数，这样方法将会根据正则表达式去拆分字符串
- 这个方法即使不指定全局匹配，也会全都拆分
```
var str = "1a2b3c4d5e6f7";
       
//根据任意字母来将字符串拆分
var result = str.split(/[A-z]/);
alert(result);

实行结果：
1,2,3,4,5,6,7
```
#### 34.3.2 `search()`
- 可以搜索字符串中是否含有指定内容
- 如果搜索到指定内容，则会返回第一次出现的索引，如果没有搜索到返回-1
- serach()只会查找第一个，即使设置全局匹配也没用
```
var str = "hello abc hello abc";
var result = str.search("abc");

alert(result);

实行结果：
6
```
- 它可以接收一个正则表达式作为参数，然后会根据正则表达式去检索字符串
```
//搜索字符串中是否含有abc 或aec 或afc
var str = "hello abc hello aec hello afc";
var result = str.search(/a[bef]c/);

alert(result);

实行结果：
6
```
#### 34.3.3 `match()`
- 可以根据正则表达式，从一个字符串中将符合条件的内容提取出来。
- 默认情况下我们的`match()`只会找到第一个符合要求的内容，找到以后就停止检索
- 我们可以设置正则表达式为全局匹配模式，这样就会匹配到所有的内容
- 可以为一个正则表达式设置多个匹配模式，且顺序无所谓
```
var str = "1a2b3c4d5e6f78A9B ";
//设置正则表达式为全局匹配模式
var result = str.match(/[a-z]/g);
        
alert(result);

实行结果：
a,b,c,d,e,f
```
```
var str = "1a2b3c4d5e6f78A9B";
//设置正则表达式为全局匹配模式，并且忽略大小写
var result = str.match(/[a-z]/ig);
        
alert(result);

实行结果：
a,b,c,d,e,f,A,B
```
- `match()`会将匹配到的内容封装到一个数组中返回，即使只查询到一个结果
```
var str = "1a2b3c4d5e6f78A9B";
//设置正则表达式为全局匹配模式，并且忽略大小写
var result = str.match(/[a-z]/ig);

//判断是否是一个数组        
alert(Array.isArray(result));
alert(result[0]);

实行结果：
true
a
```
#### 34.3.4 `replace()`
- 可以将字符串中指定内容替换成新的内容
- 参数
  - 第一个，被替换的内容，可以接收一个正则表达式作为参数
  - 第二个，新的内容
- 默认只会替换第一个
```
var str = "1a2a3a4d5e6f78A9B";
var result = str.replace("a","^_^");
        
alert(result);

实行结果：
1^_^2a3a4d5e6f78A9B
```
```
var str = "1a2a3a4d5e6f78A9B";
//设置正则表达式为全局匹配模式，并且忽略大小写
var result = str.replace(/a/ig,"^_^");
        
alert(result);

实行结果：
1^_^2^_^3^_^4d5e6f78^_^9B
```
```
//将所有的字母都替换成^_^
var str = "1a2a3a4d5e6f78A9B";
var result = str.replace(/[a-z]/ig,"^_^");
        
alert(result);

实行结果：
1^_^2^_^3^_^4^_^5^_^6^_^78^_^9^_^
```
```
var str = "1a2a3a4d5e6f78A9B";
var result = str.replace(/[a-z]/ig,"");
        
alert(result);

实行结果 ：
123456789
```
### 34.4 语法补充
#### 34.4.1 量词
- 通过量词可以设置一个内容出现的次数
- 量词只对它前边的一个内容起作用
- `{n}` 正好出现n次

```
//创建一个正则表达式检查一个字符串中是否含有`aaa`
var reg = /a{3}/;
alert(reg.test("aaabc"));

实行结果：
true
```
```
//创建一个正则表达式检查一个字符串中是否含有`ababab`
var reg = /(ab){3}/;
alert(reg.test("abababc"));

实行结果：
true
```
- `{m,n}` 出现`m-n`次
```
//创建一个正则表达式检查一个字符串中是否含有`ab(出现1到3次)c`
var reg = /ab{1,3}c/;
alert(reg.test("abbc"));

实行结果：
true
```
- `{m,}` 出现`m`次以上
- `+` 至少一个，相当于`{1,}`
- `*` 0个或多个，相当于`{0,}`
- `?` 0个或1个，相当于`{0,1}`
#### 34.4.2 其他
- `^` 表示开头 
```
//判断字符串的首字母是否是a
var reg = /^a/;
alert(reg.test("bcabc"));

实行结果：
false
```
- `$` 表示结尾
```
//判断字符串的结尾字母是否是c
var reg = /c$/;
alert(reg.test("abcabc"));

实行结果：
true
```
- 如果在正则表达式中同时使用`^$`，则要求字符串必须完全符合正则表达式
```
//以下表达式只能是a自己
var reg = /^a$/;

alert(reg.test("aaa"));

实行结果：
false
```
练习：判断一个手机号是否是正确的手机号
```
/* 手机号的规则：
  11位数
  第一位：开头是1 ---> ^1
  第二位：3-9任意数字 ---> [3-9]
  第三位以后：任意数字9个 ---> [0-9]{9}$
*/
var phoneNum = "13567890123";
var phoneReg = /^1[3-9][0-9]{9}$/

alert(phoneReg.test(phoneNum));

实行结果：
true 
```
- `.` 表示任意字符
  - 在正则表达式中使用`\`作为转义字符
  - 所以查找字符串中是否含有`.`，则需要写成`\.`
  - 注意：使用构造函数时，由于它的参数是一个字符串，而`\`是字符串中转义字符，如果要使用`\`，则需要使用`\\`来代替
```
//使用字面量
var reg = /\./;
alert(reg.test("b.a"));

实行结果：
true
```
```
//使用构造函数
var reg = new RegExp("\\.");
alert(reg.test("b.a"));

实行结果：
true
```
- `\w` 表示任意字母，数字，下划线 --> [A-z0-9_]
- `\W` 除了字母，数字，下划线 --> [^A-z0-9_] 
- `\d` 表示任意的数字 --> [0-9]
- `\D` 除了数字
- `\s` 表示空格
- `\S` 除了空格
- `\b` 单词边界
```
//创建一个正则表达式检查一个字符串中是否含有单词child
var reg = /\bchild\b/;
alert(reg.test("hello children"));

实行结果：
false 
```
- `\B` 除了单词边界
- `/^\s*|\s*$/g` 匹配开头和结尾的空格
```
//去掉开头的空格
str = str.replace(/^\s*/,"");

//去掉结尾的空格
str = str.replace(/\s*$/,"");

//去掉字符串中的前后的空格
str = str.replace(/^\s*|\s*$/g,"");
```
### 34.5 练习：邮件的正则
```
//判断电子邮件是否合法
/*
  电子邮件:  
      hello     .nihao     @     abc     .com     .cn
      1 hello --> 任意字母数字下划线 --> \w{3,} 
      2 .nihao --> .任意字母数字下划线 --> (\.\w+)*
      3 @ --> @ --> @
      4 abc --> 任意字母数字 --> [A-z0-9]+
      5 .com --> .任意字母(2-5位) --> (\.[A-z]{2,5}){1,2}
      6 .cn --> .任意字母(2-5位)
*/

var emailReg = /^\w{3,}(\.\w+)*@[A-z0-9]+(\.[A-z]{2,5}){1,2}$/
var email = "abc.abc@abc.com";

alert(emailReg.test(email));

实行结果：
true
```
## 35. DOM
### 35.1 简介
DOM，全称是：Document Object Model，文档对象模型。js中通过DOM来对HTML文档进行操作，只要理解了DOM就可以随心所欲的操作WEB页面。
- 文档
  - 文档表示的就是整个的HTML网页文档
- 对象
  - 对象表示将网页中的每一个部分都转换为了一个对象
- 模型
  - 使用模型来表示对象之间的关系，这样方便我们获取对象
### 35.2 节点：Node
- 构成网页的最基本的组成部分，网页中的每一个部分都可以称为是一个节点。
- 比如：html标签，属性，文本，注释，整个文档等都是一个节点
- 虽然都是节点，但是实际上他们的具体类型是不同的。常用节点分为四类：
  - 文档节点：整个HTML文档
  - 元素节点：HTML文档中的HTML标签
  - 属性节点：元素的属性
  - 文本节点：HTML标签中的文本内容
  - 节点的类型不同，属性和方法也都不尽相同
- nodeName
  - 文档节点：`#document`
  - 元素节点：标签名
  - 属性节点：属性名
  - 文本节点：`#text`
- nodeType
  - 文档节点：`9`
  - 元素节点：`1`
  - 属性节点：`2`
  - 文本节点：`3`
- nodeValue
  - 文档节点：`null`
  - 元素节点：`null`
  - 属性节点：属性值 
  - 文本节点：文本内容
#### 35.2.1 文档节点
浏览器已经为我们提供了文档节点对象，这个对象是`window`属性。 <br/>
可以在页面中直接使用，文档节点代表的是整个网页。<br/>
```
//用js将按钮改为button
<button id="btn">按钮</button>
<script>
  //获取到button对象
  var btn = document.getElementById("btn");

  //修改按钮中的文字
  btn.innerHTML = "button";
</script>
```
### 35.3 事件
- 事件就是文档或浏览器窗口中发生的一些特定的交互瞬间。
- JavaScript与HTML之间的交互是通过事件实现的。
- 对于Web应用来说，有下面这些代表性的事件
  - 点击某个元素
  - 将鼠标移动至某个元素上方
  - 按下键盘上的某个键
  - 关闭窗口...
- 我们可以在事件对应的属性中设置一些js代码，这样当事件被触发时，这些代码将会执行
- 以下写法我们叫做结构和行为耦合，不方便维护，不推荐使用
```
<button id="btn" onmousemove="alert('鼠标已滑动到按钮处')">按钮</button>

实行结果：
鼠标滑过按钮处，显示"鼠标已滑动到按钮处"
```
- 可以为按钮的对应事件绑定处理函数的形式来响应事件
  - 当事件被触发时，其对应的函数将会被调用
```
<button id="btn">按钮</button>
<script>
  //获取到button对象
  var btn = document.getElementById("btn");

  //绑定一个移动事件
  //这种移动事件绑定的函数，我们称为移动  响应函数
  btn.onmousemove = function(){
    alert("鼠标已滑动到按钮处");
  }
</script>

实行结果：
鼠标滑过按钮处，显示"鼠标已滑动到按钮处"
```
### 35.4 文档的加载
- `onload`事件会在整个页面加载完成之后才触发
- 为`window`绑定一个`onload`事件，该事件对应的响应函数将会在页面加载完成之后执行
- 这样可以确保我们的代码执行时所有的DOM对象已经加载完毕了
```
<head>
  <script>
    window.onload = function () {
      //获取到button对象
      var btn = document.getElementById("btn");

      //绑定一个移动事件
      btn.onmousemove = function () {
        alert("鼠标已滑动到按钮处");
      }
    }
  </script>
</head>
<body>
  <button id="btn">按钮</button>
</body>

实行结果：
鼠标滑过按钮处，显示"鼠标已滑动到按钮处"
```
### 35.5 DOM方法查询
#### 35.5.1 获取元素节点
通过`document`对象调用。<br/>
- `getElementById()`
  - 通过`id`属性获取一个元素节点对象
- `getElementsByTagName()`
  - 通过`标签名`获取一组元素节点对象
- `getElementsByName()`
  - 通过`name`属性获取一组元素节点对象
#### 35.5.2 获取元素节点的子节点
通过具体的`元素节点`调用。<br/>
- `getElementsByTagName()`
  - 方法，返回当前节点的指定标签名后代节点
- `childNodes`
  - 属性，表示当前节点的所有子节点
  - 会获取包括文本节点在内的所有节点
  - 根据DOM标签，标签减空白也会当成文本节点
  - 注意：在IE8及以下的浏览器中，不会将空白文本当成子节点
- 追加：`children`
  - 属性，可以获取当前元素的所有子元素(不是节点)
- `firstChild`
  - 属性，表示当前节点的第一个子节点
  - 可以获取到当前元素的第一个子节点(包括空白文本节点)
- 追加：`firstElementChild`
  - 属性，可以获取当前元素的第一个子元素
  - 不支持IE8及以下的浏览器。如果要兼容尽量避免使用
- `lastChild`
  - 属性，表示当前节点的最后一个子节点
#### 35.5.3 获取父节点和兄弟节点
通过具体的节点调用 <br/>
- `parentNode`
  - 属性，表示当前节点的父节点
- `previousSibling`
  - 属性，表示当前节点的前一个兄弟节点
  - 也可能获取到空白的文本
- 追加：`previousElementsSibling`
  - 属性，获取前一个兄弟元素
  - IE8及以下不支持
- `nextSibling`
  - 属性，表示当前节点的后一个兄弟节点
#### 35.5.4 追加知识点
- `innerHTML`
  - 该属性可以获取到元素内部的文本内容
- `innerText`
  - 该属性可以获取到元素内部的文本内容
  - 它和`innerHTML`类似，不同的是它会自动将`html`的标签去除
#### 35.5.5 DOM其他查询方法
```
//获取body标签
var body = document.getElementsByTagName("body")[0];
```
- 在`document`中有一个属性`body`，它保存的是`body`的引用
- 所以以上代码可以改成如下代码：
```
var body = document.body;
console.log(body);

实行结果：
[object HTMLBodyElement]
```
- `document.documentElement`保存的是`html`根标签
```
var html = document.documentElement;
console.log(html);

实行结果：
[object HTMLHtmlElement]
```
- `document.all`代表页面中所有的元素
```
var all = document.all;

//获取页面中所有的元素
for (var i = 0; i < all.length; i++) {
  console.log(all[i]);
}
```
- 根据元素的`class`属性值查询一组元素节点对象
```
var box1 = ducument.getElementsByClassName("box1");
```
- `document.querySelector()`
  - 需要一个选择器的字符串作为参数，可以根据一个CSS选择器来查询一个元素节点对象
  - 虽然IE8中没有`getElementsByClassName()`，但是可以使用`querySelector()`代替
  - 使用该方法总会返回唯一的一个元素，如果满足条件的元素有多个，那么它只会返回第一个
```
</head>
  <script>
    window.onload = function () {
      var div = document.querySelector(".box1 div");
      alert(div.innerHTML);
    }
  </script>
</head>
<body>
  <div class="box1">
    <div>我是box1中的div</div>
  </div>
  <div class="box2"></div>
  <div class="box3"></div>
</body>

实行结果：
我是box1中的div
```
- `document.querySelectorAll()`
  - 该方法和`querySelector()`用法类似，不同的是它会将符合条件的元素封装到一个数组中返回
  - 即使符合条件的元素只有一个，它也会返回数组
```
<head>
  <script>
    window.onload = function () {
      var box1 = document.querySelectorAll(".box1");
      alert(box1.length);
    }
  </script>
</head>
<body>
  <div class="box1">
    <div>我是box1中的div</div>
  </div>
  <div class="box1">
    <div>我是box1中的div</div>
  </div>
  <div class="box1">
    <div>我是box1中的div</div>
  </div>
</body>

实行结果：
3
```
### 35.6 DOM增删改
- `document.createElement()`
  - 可以用于创建一个元素节点对象
  - 它需要一个标签名作为参数，将会根据该标签名创建元素节点对象
  - 并将创建好的对象作为返回值返回
- `document.createTextNode()`
  - 可以用来创建一个文本节点对象
  - 需要一个文本内容作为参数，将会根据内容创建文本节点，并将新的节点返回
- `appendChild()`
  - 向一个父节点中添加一个新的子节点
  - 语法：`父节点.appenChild(子节点);`
  - 常用语法：`子节点.parentNode.appenChild(子节点);`
- `insertBefore()` 
  - 可以在指定的子节点前插入新的子节点
  - 语法：`父节点.insertBefore(新节点,旧节点);`
- `replaceChild()`
  - 可以使用指定的子节点替换已有的子节点
  - 语法：`父节点.replace(新节点,旧节点);`
- `removeChild()`
  - 可以删除一个子节点
  - 语法：`父节点.removeChild(子节点);` (属于它杀)
  - 常用语法：`子节点.parentNode.removeChild(子节点);` (属于自杀)
- 使用`innerHTML`也可以完成DOM的增删改的相关操作
  - 一般我们会两种方法结合使用
  - 所以可以将以下代码改为：
```
//创建一个“广州”节点: <li>广州</li>

//1. 创建li元素节点
var gzli = document.createElement("li");

//2. 创建广州文本节点
var gzText = document.createTextNode("广州");

//3. 将gzText设置为li的子节点
gzli.append(gzText);
```
```
//1. 创建li元素节点
var gzli = document.createElement("li");

//2. 将文本插入到li标签中
gzli.innerHTML = "广州";
```
- 追加：`confirm()`：用于弹出一个带有确认和取消按钮的提示框
  - 需要一个字符串作为参数，该字符串将会作为提示文字显示出来
  - 如果用户点击确认则会返回`true`，如果点击取消则返回`false`
- 练习`19_dom3.html`注意点
  - `for`循环会在页面加载完成之后立即执行
  - 而响应函数会在超链接被点击时才执行
  - 当响应函数执行时，`for`循环早已执行完毕
```
for(var i = 0; i < allA.length; i++){
  alert("for循环正在执行" + i);

  allA[i].onclick = function(){
  
    alert("响应函数正在执行" + i);
  
    return false;
  }
}

实行结果：

for循环正在执行0
for循环正在执行1
for循环正在执行2
响应函数正在执行3
```
## 36. DOM操作CSS
### 36.1 通过js修改元素的样式
- 语法：`元素.style.样式名 = 样式值;`
- 注意：如果CSS样式中含有`-`，这种名称在js中是不合法的
  - 比如：`background-color`
  - 需要将这种样式名修改为驼峰命名法
  - 去掉`-`，然后将`-`后的字母大写
- 我们通过`style`属性设置的样式都是内联样式，而内联样式有较高的优先级，所以通过js修改的样式往往会立即显示
- 但是如果在样式中写了`!important`，则此时样式会有最高的优先级，即使通过js也不能覆盖该样式，此时将会导致js修改样式失效
- 所以尽量不要为样式添加`!important`。
```
</head>
  <style>
    #box1 {
      width: 100px;
      height: 100px;
      background-color: brown;
      margin-top: 20px;
    }
  </style>
  <script>
    window.onload = function () {
      //获取按钮
      var btn = document.getElementById("btn");
      //绑定单击响应函数
      btn.onclick = function(){
        box1.style.width = "200px";
        box1.style.height = "200px";
        box1.style.backgroundColor = "blue";
      }
    }
  </script>
</head>
<body>
    <button id="btn">按钮</button>
    <div id=box1></div>
</body>
```
### 36.2 通过js读取元素的样式
#### 36.2.1 读取内联样式
- 语法：`元素.style.样式名`
- 注意：通过`style`属性设置和读取的都是内联样式，无法读取样式表中的样式
```
<head>
  <style>
    #box1 {
      width: 100px;
      height: 100px;
      background-color: brown;
      margin-top: 20px;
    }
  </style>
  <script>
    window.onload = function () {
      //获取按钮1
      var btn1 = document.getElementById("btn1");
      //绑定单击响应函数
      btn1.onclick = function(){
        box1.style.width = "200px";
        box1.style.height = "200px";
        box1.style.backgroundColor = "blue";
      }
      //点击按钮2，读取元素的样式
      var btn2 = document.getElementById("btn2");
      btn2.onclick = function(){
        alert(box1.style.width);
        }
      }
  </script>
</head>
<body>
    <button id="btn1">按钮1</button>
    <button id="btn2">按钮2</button>
    <div id=box1></div>
</body>

实行流程：
只有点击按钮1之后点击按钮2才能显示box1的宽度
因为"元素.style.样式名"读取的都是内联样式，
点击按钮1之后，样式被写入内联样式，所以可以读取
```
#### 36.2.2 读取元素当前显示的样式(仅IE支持)
- 语法：`元素.currentStyle.样式名`
- 它可以用来读取当前元素正在显示的样式
- 如果当前元素没有设置该样式，则获取它的默认值
- `currentStyle`只有IE浏览器支持，其他的浏览器都不支持
```
<head>
  <style>
    #box1 {
      width: 100px;
      height: 100px;
      background-color: brown;
      margin-top: 20px;
    }
  </style>
  <script>
    window.onload = function () {
      //获取id为box1的元素
      var box1 = document.getElementById("box1");
      //获取按钮1
      var btn1 = document.getElementById("btn1");
      //绑定单击响应函数
      btn1.onclick = function () {
        alert(box1.currentStyle.width);
      }
    }
  </script>
</head>
<body>
  <button id="btn1">按钮1</button>
  <div id="box1"></div>
</body>
```
#### 36.2.3 读取元素当前显示的样式(其它浏览器支持(包括IE9以上))
- 可以使用`getComputedStyle()`这个方法来获取当前的样式
- 这个方法是`window`的方法，可以直接使用
- 需要两个参数
  - 要获取样式的元素
  - 可以传递一个伪元素，一般都传`null`
- 该方法会返回一个对象，对象中封装了当前元素对应的样式
```
<head>
  <style>
    #box1 {
      width: 100px;
      height: 100px;
      background-color: brown;
      margin-top: 20px;
    }
  </style>
  <script>
    window.onload = function () {
      //获取id为box1的元素
      // var box1 = document.getElementById("box1");
      //获取按钮1
      var btn1 = document.getElementById("btn1");
      //绑定单击响应函数
      btn1.onclick = function () {
        var obj = getComputedStyle(box1,null);
        alert(obj.width);
      }
    }
  </script>
</head>
<body>
  <button id="btn1">按钮1</button>
  <div id="box1"></div>
</body>
```
- 可以通过`对象.样式名`来读取样式
- 如果获取的样式没有设置，则会获取到真实的值，而不是默认值
- 比如：没有设置`width`，它不会获取到`auto`，而是一个长度
```
//获取一个没有设置width的box1，输出它的长度
alert(getComputeStyle(box1,null).width);

实行结果：
获取整个页面的宽度
```
- 注意：通过`currentStyle`和`getComputedStyle()`读取到的样式都是只读的，不能修改
- 如果要修改必须通过`style`属性
#### 36.2.4 读取元素当前显示的样式(既支持IE8以下浏览器也支持其它浏览器)
- 定义一个函数，用来获取指定元素的当前的样式
- 参数：
  - `obj`：要获取样式的元素
  - `name`：要获取的样式名
```
<head>
  <style>
    #box1 {
      width: 100px;
      height: 100px;
      background-color: brown;
      margin-top: 20px;
    }
  </style>
  <script>
    window.onload = function () {
      //获取按钮1
      var btn1 = document.getElementById("btn1");
      //绑定单击响应函数
      btn1.onclick = function () {
        alert(getStyle(box1,"width"));
      }
    }
    function getStyle(obj,name){
      if(window.getComputedStyle){
        //正常浏览器的方式，具有getComputedStyle()方法
        return getComputedStyle(obj,null)[name];
      }else{
        //IE8的方式，没有getComputedStyle()方法
        return obj.currentStyle[name];
      }
    }
  </script>
</head>
<body>
  <button id="btn1">按钮1</button>
  <div id="box1"></div>
</body>

实行结果：
100px
```
### 36.3 其他样式操作的属性
#### 36.3.1 `clientWidth`和`clientHeight`
- 这两个属性可以获取元素的可见宽度和高度
- 这些属性都是不带`px`的，返回的都是一个数字，可以直接进行计算
- 会获取元素宽度和高度，包括内容区和内边距
- 这些属性都是只读的不能修改
```
<head>
  <style>
    #box1 {
      width: 100px;
      height: 100px;
      padding:10px;
      border: 10px solid yellow;
      background-color: red;
    }
  </style>
  <script>
    window.onload = function(){
      var box1 = document.getElementById("box1");
      var btn1 = document.getElementById("btn1");
      btn1.onclick = function(){
        alert(box1.clientWidth);
        alert(box1.clientHeight);
      }
    }
  </script>
</head>
<body>
  <button id="btn1">点我一下</button>
  <br /><br />
  <div id="box1"></div>
</body>

实行结果：120
```
#### 36.3.2 `offsetWidth`和`offsetHeight`
- 可以获取元素的整个宽度和高度，包括内容区，内边距和边框
```
alert(box1.offsetWidth);
alert(box1.offsetHeight);
```
#### 36.3.3 `offsetParent`,`offsetLeft`,`offsetTop`
- `offsetParent`
  - 可以用来获取当前元素的定位父元素
  - 会获取到离当前元素最近的开启了定位的祖先元素
    - 如果所有的祖先元素都没有开启定位，则返回`body`
```
var op = box1.offsetParent;
```
- `offsetLeft`
  - 当前元素相对与其定位元素的水平偏移量
- `offsetTop`
  - 当前元素相对与其定位元素的垂直偏移量
```
<head>
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            padding: 10px;
            border: 10px solid yellow;
            background-color: red;
        }
        #box2{
            padding:100px;
            background-color: #bfa;
        }
    </style>
    <script>
        window.onload = function () {
            var box1 = document.getElementById("box1");
            var btn1 = document.getElementById("btn1");
            btn1.onclick = function () {
                alert(box1.offsetLeft);
            }
        }
    </script>
</head>
<body>
    <button id="btn1">点我一下</button>
    <br /><br />
    <div id="box3">
        <div id="box2" style="position: relative;">
            <div id="box1">
            </div>
        </div>
    </div>
</body>

实行结果：
100
```
#### 36.3.4 `scrollWidth`和`scrollHeight`
- 可以获取元素整个滚动区域的宽度和高度
```
<head>
    <style>
        #box4 {
            width: 200px;
            height: 300px;
            background-color: #bfa;
            overflow: auto;
        }
        #box5 {
            width: 450px;
            height: 600px;
            background-color: #fba;
        }
    </style>
    <script>
        window.onload = function () {
            var box1 = document.getElementById("box1");
            var btn1 = document.getElementById("btn1");
            btn1.onclick = function () {
                alert(box4.scrollWidth);
                alert(box4.scrollHeight);
            }
        }
    </script>
</head>
<body>
    <button id="btn1">点我一下</button>
    <br /><br />
    <div id="box4">
        <div id="box5"></div>
    </div>
</body>

实行结果：
450
600
```
#### 36.3.5 `scrollLeft`和`scrollTop`
- `scrollLeft`：可以获取水平滚动条滚动的距离
```
alert(box4.scrollLeft);
```
-　`scrollTop`：可以获取垂直滚动条滚动的距离
```
alert(box4.scrollTop);
```
```
<head>
    <style>
        #box4 {
            width: 200px;
            height: 300px;
            background-color: #bfa;
            overflow: auto;
        }
        #box5 {
            width: 300px;
            height: 600px;
            background-color: #fba;
        }
    </style>
    <script>
        window.onload = function () {
            var box1 = document.getElementById("box1");
            var btn1 = document.getElementById("btn1");
            btn1.onclick = function () {
                // alert(box4.scrollWidth); //300
                // alert(box4.scrollHeight); //600
                // alert(box4.clientWidth); //200
                // alert(box4.clientHeight); //300

                //当满足scrollHeight-scrollTop == clientHeight
                //说明垂直滚动条滚动到底了
                alert(box4.scrollHeight - box4.scrollTop); //300

                //当满足scrollWidth-scrollLeft == clientWidth
                //说明水平滚动条滚动到底了
                alert(box4.scrollWidth - box4.scrollLeft); //200
            }
        }
    </script>
</head>
<body>
    <button id="btn1">点我一下</button>
    <br /><br />
    <div id="box4">
        <div id="box5"></div>
    </div>
</body>

实行结果：
300
200
```
- `onsrcoll`：该事件会在元素的滚动条滚动时触发
```
<head>
    <style>
        #info {
            width: 500px;
            height: 500px;
            background-color: #fba;
            overflow: auto;
            font-size: 14px;
        }
    </style>
    <script>
        window.onload = function () {
            /*
                当垂直滚动条滚动到底时，使表单项可用
            */
            //获取info
            var info = document.getElementById("info");
            //为info绑定一个滚动条滚动事件
            info.onscroll = function () {
                //获取表单
                var checkbox = document.getElementById("checkbox");
                var submit = document.getElementById("submit");
                // var input1 = document.getElementsByTagName("input")[0];
                // var input2 = document.getElementsByTagName("input")[1];
                //当垂直滚动条滚动到底时，表单可用
                if (this.scrollHeight - this.scrollTop == this.clientHeight) {
                    /*
                        disabled属性可以设置一个元素是否禁用
                            如果设置为true，则元素禁用
                            如果设置为false，则元素可用
                    */
                    checkbox.disabled = false;
                    submit.disabled = false;
                    // input1.disabled = false;
                    // input2.disabled = false;
                }
            }
        }
    </script>
</head>
<body>
    <h3>网站用户注册协议书</h3>
    <p id="info">
        亲爱的用户，欢迎注册此网站！<br />
        注册此网站前需要阅读以下条款：<br />
        1. 本站运用自己的操作系统，禁止转载或非法使用不正当手段编撰此网站的内容。<br />
        2. 本站对注册用户的电子邮件，手机号等隐私材料进行保护，承诺不会在为获得注册用户许可的情况下将用户的个人资料信息出租或出售给第三方。<br />
        3. 关于注册用户隐私的具体协议以本站的隐私声明为准。如果注册用户提供的资料包含不正确的信息，本站将结束注册用户使用网络服务资格的权利。<br />
        4. 注册用户一旦注册成功，成本本站的合法的注册用户。您可随时根据需要修改用户密码。<br />
        5. 每个注册用户都要以其注册用户名进行的所有活动和事件负全责。<br />
        6. 基于本站提供的网络服务的重要性，注册用户应同意：提供详尽，准确的个人资料。若个人信息有所改变，请即使更新内容。<br />
        7. 本站运用自己的操作系统通过国际互联网为注册用户提供网络服务。<br />
        8. 本站的各项电子服务的所有权和运作权归本站所有。<br />
        9. 本协议条款是处理双方权利义务的当然约定一句，除非违反国家强制性法律，否则始终有效。<br />
        10. 由于注册用户协议变更后因未熟悉规定而引起的损失，本站将不会承担任何责任。<br />
        11. 本站运用自己的操作系统，禁止转载或非法使用不正当手段编撰此网站的内容。<br />
        12. 本站对注册用户的电子邮件，手机号等隐私材料进行保护，承诺不会在为获得注册用户许可的情况下将用户的个人资料信息出租或出售给第三方。<br />
        13. 关于注册用户隐私的具体协议以本站的隐私声明为准。如果注册用户提供的资料包含不正确的信息，本站将结束注册用户使用网络服务资格的权利。<br />
        14. 注册用户一旦注册成功，成本本站的合法的注册用户。您可随时根据需要修改用户密码。<br />
        15. 每个注册用户都要以其注册用户名进行的所有活动和事件负全责。<br />
        16. 基于本站提供的网络服务的重要性，注册用户应同意：提供详尽，准确的个人资料。若个人信息有所改变，请即使更新内容。<br />
        17. 本站运用自己的操作系统通过国际互联网为注册用户提供网络服务。<br />
        18. 本站的各项电子服务的所有权和运作权归本站所有。<br />
        19. 本协议条款是处理双方权利义务的当然约定一句，除非违反国家强制性法律，否则始终有效。<br />
        20. 由于注册用户协议变更后因未熟悉规定而引起的损失，本站将不会承担任何责任。<br />
    </p>
    <input id="checkbox" type="checkbox" disabled="disabled" />我已阅读并遵守此协议
    <input id="submit" type="submit" value="注册" disabled="disabled" />
</body>
```
### 36.4 事件
#### 36.4.1 事件对象
- 当事件的响应函数被触发时，浏览器每次都会将一个事件对象作为实参传递进响应函数。
- 在事件对象中封装了当前事件相关的一切信息
- 比如：鼠标的坐标，键盘哪个按键被按下，鼠标滚轮滚动的方向
- `onmousemove`：该事件将会在鼠标在元素中移动时被触发
- `clientX`：可以获取鼠标指针的水平坐标
- `clientY`：可以获取鼠标指针的垂直坐标
```
//鼠标滑过areaDiv，将在showMsg中显示鼠标指针的坐标
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>事件对象</title>
    <style>
        #areaDiv{
            width: 300px;
            height: 80px;
            border: 1px solid black;
        }
        #showMsg{
            margin-top: 20px;
            width: 300px;
            height: 30px;
            border: 1px solid black;
        }
    </style>
    <script>
        window.onload = function(){
            var areaDiv = document.getElementById("areaDiv");
            var showMsg = document.getElementById("showMsg");

            areaDiv.onmousemove = function(event){
                var x = event.clientX;
                var y = event.clientY;

                //在showMsg中显示鼠标的坐标
                showMsg.innerHTML = "x = " + x + ", y = " + y;
            }
        }
    </script>
</head>
```
- 在IE8中，响应函数被触发时，浏览器不会传递事件对象
- 在IE8及以下的浏览器中，是将事件对象作为`window`对象的属性保存的
```
//鼠标滑过areaDiv，将在showMsg中显示鼠标指针的坐标
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>事件对象</title>
    <style>
        #areaDiv{
            width: 300px;
            height: 80px;
            border: 1px solid black;
        }
        #showMsg{
            margin-top: 20px;
            width: 300px;
            height: 30px;
            border: 1px solid black;
        }
    </style>
    <script>
        window.onload = function(){
            var areaDiv = document.getElementById("areaDiv");
            var showMsg = document.getElementById("showMsg");

            //解决事件对象的兼容性问题 
            //如果浏览器是IE8以下
            /*
            if(!event){
              event = window.event;
            }
            */

            event = event || window.event;

            areaDiv.onmousemove = function(event){
                var x = event.clientX;
                var y = event.clientY;

                //在showMsg中显示鼠标的坐标
                showMsg.innerHTML = "x = " + x + ", y = " + y;
            }
        }
    </script>
</head>
```
#### 36.4.2 `div`跟随鼠标移动
- `clientX`和`clientY`：用于获取鼠标在当前的可见窗口的坐标
- `div`的偏移量，是相对于整个页面的。
- `pageX`和`pageY`可以获取鼠标相对于当前页面的坐标。
  - 这两个属性在IE8中不支持，所以如果需要兼容IE8，则不要使用
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>盒子随着鼠标的移动而移动</title>
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            background-color: red;

            /*
                开启box1的绝对定位
            */
            position: absolute;
        }
    </style>
    <script>
        window.onload = function () {
            /*
               使div可以跟随鼠标移动
            */

            //获取box1
            var box1 = document.getElementById("box1");
            //绑定鼠标移动事件
            document.onmousemove = function (event) {
                //解决兼容问题
                event = event || window.event;
                /*
                    chrome认为浏览器的滚动条是body的，可以通过body.srollTop来获取
                    火狐等浏览器认为浏览器的滚动条是html的
                */

                var sTop = document.body.scrollTop || document.documentElement.scrollTop;
                var sLeft = document.body.scrollLeft || document.documentElement.scrollLeft;

                //获取鼠标坐标
                var left = event.clientX;
                var top = event.clientY; 

                //设置div的偏移量
                box1.style.left = left + sLeft + "px";
                box1.style.top = top + sTop + "px";
            }
        }
    </script>
</head>
<body style="height: 1000px; width:2000px">
    <div id="box1"></div>
</body>
```
#### 36.4.2 事件的冒泡：Bubble
- 所谓的冒泡指的就是事件的向上传导，当后代元素上的事件被触发时，其祖先元素的相同事件也会被触发
- 在开发中大部分情况冒泡都是有用的，如果不希望发生事件冒泡可以通过事件对象来取消冒泡
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>事件的冒泡</title>
    <style>
        #box1{
            width: 200px;
            height: 200px;
            background-color: yellowgreen;
        }
        #s1{
            background-color: yellow;
        }
    </style>
    <script>
        window.onload = function(){
            //为s1绑定一个点击响应函数
            var s1 = document.getElementById("s1");
            s1.onclick = function(event){

                event = event || window.event;
                alert("我是span的单击响应函数");

                //取消冒泡
                //可以将事件对象的cancelBubble设置为true，即可取消冒泡
                event.cancelBubble = true;
            }
            //为box1绑定一个点击响应函数
            var box1 = document.getElementById("box1");
            box1.onclick = function(event){
                event = event || window.event;
                alert("我是div的单击响应函数");
                event.cancelBubble = true;
            }
            //为body绑定一个单击响应函数
            document.body.onclick = function(){
                alert("我是body的单击响应函数");
            }
        }
    </script>
</head>
<body>
    <div id="box1">我是box1
        <span id="s1">我是span</span>
    </div>
</body>
```
#### 36.4.3 事件的委派
- 指将事件统一绑定给元素的共同的祖先元素，这样当后代元素上的事件触发时，会一直冒泡到祖先元素
- 从而通过祖先元素的响应函数来处理事件。
- 事件委派是利用了冒泡，通过委派可以减少事件绑定的次数，提高程序的性能。
- `target`：`event`中的`target`表示的是触发事件的对象
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>事件的委派</title>
    <script>
        window.onload = function () {
            //点击按钮添加超链接
            var btn1 = document.getElementById("btn1");
            var ul = document.getElementById("ul");
            btn1.onclick = function () {
                //创建一个超链接
                var li = document.createElement("li");
                li.innerHTML = "<a href='javascript:;' class='link'>新建的超链接</a>";

                //将新建的li添加到ul中
                ul.appendChild(li);

            }
            /*
                只绑定一次事件，即可应用到多个的元素上，即使是后添加的
                我们可以尝试将其绑定给元素的共同的祖先元素
            */
            //为ul绑定一个单击响应函数
            ul.onclick = function (event) {
                //如果触发事件的对象是我们期望的元素，则执行否则不执行
                if (event.target.className == "link") {
                    alert("我是ul的单击响应函数");
                }
            }
        }
    </script>
</head>
<body>
    <button id="btn1">添加一个超链接</button>
    <ul id="ul" style="background-color: teal;">
        <li><a href="javascript:;" class="link">超链接一</a></li>
        <li><a href="javascript:;" class="link">超链接二</a></li>
        <li><a href="javascript:;" class="link">超链接三</a></li>
    </ul>
</body>
```
#### 36.4.4 事件的绑定
- 使用 `对象.事件 = 函数`的形式绑定响应函数，它只能同时为一个元素的一个事件绑定一个响应函数。
- 不能绑定多个，如果绑定了多个，则后边会覆盖前边的
- 参数：
  1. 事件的字符串，不要`on`
  2. 回调函数，当事件触发时，该函数会被调用
  3. 是否在捕获阶段触发事件，需要一个布尔值，一般都传`false`
- 使用`addEventListener()`可以同时为一个元素的相同事件同时绑定多个响应函数
- 这样当事件被触发时，响应函数将会按照函数的绑定顺序执行
- 这个方法不支持IE8及一下的浏览器 
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>事件的绑定</title>
    <script>
        window.onclick = function(){
            var btn01 = document.getElementById("btn01");
            btn01.addEventListener("click",function(){
                alert(1);
            },false );
            btn01.addEventListener("click",function(){
                alert(2);
            },false );
            btn01.addEventListener("click",function(){
                alert(3);
            },false );
        }
    </script>
</head>
<body>
    <button id="btn01">点我一下</button>
</body>
```
- `attachEvent()`：在IE8中可以使用`attachEvent()`来绑定事件
- 参数
  1. 事件的字符串，要on
  2. 回调函数
- 这个方法也可以同时为一个事件绑定多个处理函数
- 不同的是它是后绑定先执行，执行顺序和`addEventListener()`相反 
```
btn01.attachEvent("onclick",function(){
  alert(1);
});
btn01.attachEvent("onclick",function(){
  alert(2);
});
btn01.attachEvent("onclick",function(){
  alert(3);
});
```
练习：事件绑定，兼容所有版本。
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>事件的绑定</title>
    <script>
        window.onclick = function () {
            var btn01 = document.getElementById("btn01");
            //定义一个函数，用来为指定元素绑定响应函数
            /*
            addEventListener()中的this，是绑定事件的对象
            attachEvent()中的this，是window
            需要统一两个方法this
            */

            /*
            参数：
            obj：要绑定事件的对象
            eventStr：事件的字符串
            callback：回调函数
            */
            bind(btn01,"click",function(){
                alert(1);
            });
            bind(btn01,"click",function(){
                alert(2);
            });

        }
        function bind(obj, eventStr, callback) {
            if (obj.addEventListener) {
                //大部分浏览器兼容的方式
                obj.addEventListener(eventStr, callback, false);
            } else {
                /*
                 this是谁由调用方式决定
                */
                //IE8及以下版本
                obj.attachEvent("on" + eventStr, function(){
                    //在匿名函数中调用回调函数
                    callback.call(obj);
                });
            }
        }
    </script>
</head>
<body>
    <button id="btn01">点我一下</button>
</body>
```
#### 36.4.5 事件传播
关于事件的传播网景公司和微软公司有不同的理解 <br/>
- 微软公司：事件的冒泡 
  - 事件应该是由内向外传播，也就是当前事件触发时，应该先触发当前元素上的事件
  - 然后再向当前元素的祖先元素上传播，也就是说事件应该在冒泡阶段执行
- 网景公司：捕获阶段
  - 事件应该是由外向内传播，也就是当前事件触发时，应该先触发当前元素的最外层的祖先元素的事件
  - 然后再向内传播给后代元素 
- W3C综合了两个公司的方案，将事件传播分成了三个阶段
  1. 捕获阶段
    - 在捕获阶段时从最外层的祖先元素，向目标元素进行事件的捕获，但是默认此时不会触发事件 
  2. 目标阶段
    - 事件捕获到目标元素，捕获结束开始在目标元素上触发事件
  3. 冒泡阶段
    - 事件从目标元素向它的祖先元素传递，依次触发祖先上的事件 
- 如果希望在捕获阶段就触发事件，可以将`addEventListener()`的第三个参数设置为`true`
- 一般情况下我们不会在捕获阶段触发事件，所以这个参数一般都是`false`
- IE8及以下的浏览器中没有捕获阶段
#### 36.4.6 拖拽
点击鼠标可以将指定的内容随意拖拽到指定的位置。
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>拖拽</title>
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
        }
        #box2 {
            width: 100px;
            height: 100px;
            background-color: yellow;
            position: absolute;
            left: 200px;
            top: 200px;
        }
    </style>
    <script>
        window.onload = function () {
            /*
             拖拽box1元素
             1. 当鼠标在被拖拽元素上按下时，开始拖拽：onmousedown
             2. 当鼠标移动时被拖拽元素跟随鼠标移动：onmousemove
             3. 当鼠标松开时，被拖拽元素固定在当前位置：onmouseup
            */
            //获取box1元素
            var box1 = document.getElementById("box1");
            //1. 当鼠标在被拖拽元素上按下时，开始拖拽
            box1.onmousedown = function (event) {
                event = event || window.event;
                //div的水平偏移量 = 鼠标.clientX - 元素.offsetLeft
                //div的垂直偏移量 = 鼠标.clientY - 元素.offsetTop
                var ol = event.clientX - box1.offsetLeft;
                var ot = event.clientY - box1.offsetTop;

                //为document绑定一个onmousemove事件
                document.onmousemove = function (event) {
                    //2. 当鼠标移动时被拖拽元素跟随鼠标移动 
                    //解决兼容问题
                    event = event || window.event;

                    //获取鼠标坐标
                    var left = event.clientX - ol;
                    var top = event.clientY - ot;

                    //设置div的偏移量
                    box1.style.left = left + "px";
                    box1.style.top = top + "px";
                }
                //为元素绑定一个鼠标松开事件
                document.onmouseup = function () {
                    //3. 当鼠标松开时，被拖拽元素固定在当前位置：onmouseup
                    //取消document.onmousemove事件
                    document.onmousemove = null;
                    //取消document.onmouseup事件
                    document.onmouseup = null;
                    // alert("鼠标松开了");
                }
                /*
                    当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容，
                    此时会导致拖拽功能的异常，这个是浏览器提供的默认行为
                    如果不希望发生这个行为，则可以通过return false来取消默认行为
                    但是这招对IE8不起作用
                */
                return false;
            }
        }
    </script>
</head>
<body>
    我是一段文字
    <div id="box1"></div>
    <div id="box2"></div>
</body>
</html>
```
#### 36.4.7 滚轮的事件
- `onmousewheel`
  - 鼠标滚轮滚动的事件，会在滚轮滚动时触发，但是火狐不支持该属性
  - 在火狐中需要使用`DOMMouseScroll`来绑定滚动事件，该事件需要通过`addEventListener()`函数来绑定 
- `event.wheelDelta`
  - 可以获取鼠标滚轮滚动的方向
  - 向上滚正值，向下滚负值
  - `wheelDelta`这个值我们不看大小，只看正负
  - `wheelDelta`属性火狐中不支持，在火狐中使用`event.detail`来获取滚动的方向，向上滚是负值，向下滚是正值
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>滚轮事件</title>
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            background-color: red;
            margin: 20px auto;
        }
    </style>
    <script>
        window.onload = function () {
            /*
             当鼠标滚轮向下滚动时，box1变长
             当鼠标滚轮向上滚动时，box1变短
            */
            var box1 = document.getElementById("box1");
            //为box1绑定一个鼠标滚轮滚动的事件
            box1.onmousewheel = function (event) {
                /*
                当鼠标滚轮向下滚动时，box1变长
                当鼠标滚轮向上滚动时，box1变短
               */
                event = event || window.event;
                //判断鼠标滚轮滚动的方向
                //event.wheelDelta:可以获取鼠标滚轮滚动的方向，但是火狐不支持
                //向上滚正值，向下滚负值
                //在火狐中用event.detail来获取鼠标滚轮滚动的方向：向上滚负值，向下滚正值
                if (event.wheelDelta > 0 || event.detail < 0) {
                    //向上滚，box1变短
                    box1.style.height = box1.clientHeight - 10 + "px";
                } else {
                    //向下滚，box1变长
                    box1.style.height = box1.clientHeight + 10 + "px";
                }
                /*
                 使用addEventListener()方法绑定响应函数，取消默认行为时不能使用return false
                 需要使用event来取消默认行为
                 但是IE8不支持event.preventDefault();如果直接调用会报错
                */
                event.preventDefault() && event.preventDefault() ;

                /*
                 当滚轮滚动时，如果浏览器有滚动条，滚动条会随之滚动
                 这是浏览器的默认行为，如果不希望发生，则可以取消默认行为，直接return false
                */
                return false;
            }
            bind(box1, "DOMMouseScroll", box1.onmousewheel);
        }
        function bind(obj, eventStr, callback) {
            if (obj.addEventListener) {
                //大部分浏览器兼容的方式
                obj.addEventListener(eventStr, callback, false);
            } else {
                /*
                 this是谁由调用方式决定
                */
                //IE8及以下版本
                obj.attachEvent("on" + eventStr, function () {
                    //在匿名函数中调用回调函数
                    callback.call(obj);
                });
            }
        }
    </script>
</head>
<body style="height: 2000px;">
    <div id="box1"></div>
</body>
```
#### 36.4.8 键盘事件
键盘事件一般都会绑定给一些可以获取到焦点的对象或者是`document`。<br/>
- ` `：按键被按下
  - 对`onkeydown`来说如果一直按着某个按键不松手，则事件会一直触发
  - 当`onkeydown`连续触发时，第一次和第二次之间会间隔稍微长一点，其他的会非常的快
  - 这种设计是为了防止误操作的发生。
- `onkeyup`：按键被松开
- `keyCode`：可以获取按键的编码，通过它可以判断哪个按键被按下
```
//判断一个y是否被按下
document.onkeydown = function(event){
    event = event || window.event;
    //查看按键的编码
    //console.log(event.keyCode);
    //判断一个y是否被按下
    if (event.keyCode == 89) {
        alert("y键被按下了");
    }
}

实行结果：
按y键会显示y键被按下了
```
除了`keyCode`，事件对象中还提供了几个属性 <br/>
以下三个用来判断`alt`，`ctrl` 和`shift`是否被按下，如果按下则返回`true`，否则返回`false`
- `altKey`
- `ctrlKey`
- `shiftKey`
```
//判断y和ctrl是否同时被按下
window.onload = function () {
  document.onkeydown = function (event) {
    event = event || window.event;
                
    //判断y和ctrl是否同时被按下
    if (event.keyCode === 89 && event.ctrlKey) {
      alert("ctrl+y键被按下了");
    }
  }
}

实行结果：
同时按下ctrl和y键时，会弹出ctrl+y键被按下了的提示
```
- 在文本框中输入内容，属于onkeydown的默认行为
- 如果在`onkeydown`中取消了默认行为，即`return flase;`，则输入的内容，不会出现在文本框中 <br/>
练习：使文本框中不能输入数字
```
<head>
    <script>
        window.onload = function () {
            //获取input
            var input = document.getElementsByTagName("input")[0];
            input.onkeydown = function (event) {
                event = event || window.event;
                //数字48-57(注意：小键盘数字编码是96-105)
                //使文本框中不能输入数字
                if (event.keyCode >= 48 && event.keyCode <= 57) {
                    //在文本框中输入内容，属于onkeydown的默认行为
                    //如果在onkeydown中取消了默认行为，则输入的内容，不会出现在文本框中
                    return false;
                }
            }
        }
    </script>
</head>
<body>
    <input type="text"></div>
</body>
```
练习：使div可以根据不同的方向键向不同的方向移动
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>使div可以根据不同的方向键向不同的方向移动</title>
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
        }
    </style>
    <script>
        //使div可以根据不同的方向键向不同的方向移动
        /*
         按左键，div向左移动 37
         按右键，div向右移动 39
         按上键，div向上移动 38 
         按下键，div向下移动 40
        */
        window.onload = function () {
            //获取div
            var box1 = document.getElementById("box1");

            document.onkeydown = function (event) {
                event = event || window.event;

                //定义一个变量，来表示移动的速度
                var speed = 10;

                //当用户按了ctrl键以后，速度加快
                if (event.ctrlKey) {
                    speed = 50;
                }
                switch (event.keyCode) {
                    case 37:
                        //向左移，left值减小
                        box1.style.left = box1.offsetLeft - speed + "px";
                        break;
                    case 39:
                        //向右移，left值增大
                        box1.style.left = box1.offsetLeft + speed + "px";
                        break;
                    case 38:
                        //向上移，top值减小
                        box1.style.top = box1.offsetTop - speed + "px";
                        break;
                    case 40:
                        //向下移，top值增大                       
                        box1.style.top = box1.offsetTop + speed + "px";
                        break;
                }
            }
        }
    </script>
</head>
<body>
    <div id="box1"></div>
</body>
</html>
```
## 37. BOM：浏览器对象模型
- BOM可以使我们通过js来操作浏览器
- 在BOM中为我们提供了一组对象，用来完成对浏览器的操作
- BOM对象
  - `Window`：代表的是整个浏览器的窗口，同时`window`也是网页中的全局对象
  - `Navigator`：代表的是当前浏览器的信息，通过该对象可以来识别不同的浏览器
  - `Location`：代表的是当前浏览器的地址栏信息，通过`Location`可以获取地址栏信息，或者操作浏览器跳转页面
  - `History`：代表的是浏览器的历史记录，可以通过该对象来操作浏览器的历史记录。
    - 由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页
    - 而且该操作只在当次访问时有效
  - `Screen`：代表的是用户的屏幕的信息，通过该对象可以获取到用户的显示器的相关信息
- 这些BOM对象在浏览器中都是作为`window`对象的属性保存的
- 可以通过`window`对象来使用，也可以直接使用
## 37.1 `Navigator`  
- 现在`Navigator`对象中的大部分属性都已经不能帮助我们识别浏览器了
- 一般我们只会使用`userAgent`来判断浏览器的信息
  - `userAgent`是一个字符串，这个字符串中包含有用来描述浏览器信息的内容
  - 不同的浏览器会有不同的`userAgent`
  - 弹出浏览器的信息：`alert(navigator.userAgent);`
    - 火狐： Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:82.0) Gecko/20100101 Firefox/82.0
    - chrome：Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36
    - IE8/9/10：识别浏览器的关键字是`msie`
    - IE11：在IE11中已经将微软和IE相关的标识都已经去除了，所以我们基本已经不能通过`UserAgent`来识别一个浏览器是否是IE了
      - 如果通过`UserAgent`不能判断，还可以通过一些浏览器中特有的对象，来判断浏览器的信息
      - 比如：`ActiveXObject`
```
//判断浏览器是火狐，还是chrome，还是IE或是IE11
var ua = navigator.userAgent;
if (/firefox/i.test(ua)) {
  alert("你是火狐");
}else if(/chrome/i.test(ua)){
  alert("你是chrome");
}else if(/msie/i.test(ua)){
  alert("你是IE浏览器");
}else if("ActiveXObject" in window){
  alert("你是IE11浏览器");
}
```
## 37.2 `History`
对象可以用来操作浏览器向前或向后翻页。<br/>
- 属性
  - `length`：可以获取当次访问的链接的数量
- 方法
  - `back()`：可以用来回退到上一个页面，作用和浏览器的回退按钮一样
  - `forward()`：可以用来前往到下一个页面，作用和浏览器的前进按钮一样
  - `go()`：可以用来跳转到指定的页面，它需要一个整数作为参数
    - `1` 表示向前跳转一个页面，相当于`forward()`
    - `2` 表示向前跳转两个页面
    - `-1` 表示向后跳转一个页面，相当于`back()`
    - `-2` 表示向后跳转两个页面
## 37.3 `Location`
该对象中封装了浏览器的地址栏的信息。<br/>
- 如果直接打印`location`，则可以获取到地址栏的信息(当前页面的完整路径)
```
alert(location);
```
- 如果直接将`location`属性修改为一个完整的路径，或相对路径，则页面会自动跳转到该路径，并且会生成相应的历史记录
```
location = "http://www.baidu.com"; //完整路径
location = "test.html"; //相对路径
```
- 方法
  - `assign()`：用来跳转到其他的页面，作用和直接修改`location`一样
  - `location.assign("http://www.baidu.com");`
  - `reload()`：用于重新加载当前页面，作用和刷新按钮一样
    - 如果在方法中传递一个`true`，作为参数，则会强制清空缓存刷新页面
    - `location.reload(true);` 
  - `replace()`：可以使用一个新的页面替换当前页面，调用完毕也会跳转页面
    - 不会生成历史记录，不能使用回退按钮回退
    - `location.replace("test.html");`
## 38. 定时器
### 38.1 简介
如果希望一段程序，可以每间隔一段事件执行一次，乐园使用定时调用。<br/>
`setInterval()`：定时调用 <br/>
- 可以将一个函数，每隔一段时间执行一次
- 参数：
  - 回调函数，该函数会每隔一段时间被调用一次
  - 每次调用间隔的时间，单位是毫秒
- 返回值：
  - 返回一个`Number`类型的数据
  - 这个数字用来作为定时器的唯一标识
- `clearInterval()`：可以用来关闭一个定时器
  - 可以接收任意的参数
  - 如果参数是一个有效的定时器的标识，则停止对应的定时器
  - 如果参数不是一个有效的标识，则什么也不做
```
//每隔1秒调用一次function函数，当执行到11秒的时候关闭定时器
<head>
    <title>定时器</title>
    <script>
        window.onload = function () {
            //获取count
            var count = document.getElementById("count");

            //使count中的内容，自动切换
            var num = 1;
            var timer = setInterval(function () {
                count.innerHTML = num++;

                if(num == 11){
                    clearInterval(timer);
                }
            }, 1000)
        }
    </script>
</head>
<body>
    <h1 id="count"></h1>
</body>

实行结果：
定时器执行到第10秒的时候关闭
```
### 38.2 图片切换练习
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>切换图片</title>
    <script>
        window.onload = function () {
            /*
             使图片可以自动切换
            */
            //获取img标签
            var img1 = document.getElementById("img1");

            //创建一个数组来保存图片的路径
            var imgArr = ["pic/25/1.png", "pic/25/2.png", "pic/25/3.png", "pic/25/4.png", "pic/25/5.png", "pic/25/6.png"];

            //创建一个变量，用来保存当前图片的索引
            var index = 0;
            //定义一个变量，用来保存定时器的标识
            var timer;

            var btn1 = document.getElementById("btn1");
            var btn2 = document.getElementById("btn2");
            btn1.onclick = function () {
                /*
                 开启一个定时器，来自动切换图片
                 */
                timer = setInterval(function () {
                    //使索引自增
                    index++;

                    //判断索引是否超过最大索引
                    if (index >= imgArr.length) {
                        index = 0;
                    }

                    //和上面的if文一个效果
                    //index %= imgArr.length;

                    //修改img1的src属性
                    img1.src = imgArr[index];
                }, 1000);
            }
            btn2.onclick = function () {
                //点击按钮以后，停止图片的自动切换，关闭定时器
                clearInterval(timer);
            }
        }
    </script>
</head>
<body>
    <img id="img1" src="pic/25/1.png" alt="">
    <button id="btn1">开始</button>
    <button id="btn2">结束</button>
</body>
</html>
```
- 以上练习代码的不足之处：
  - 目前我们每点击一次按钮，就会开启一个定时器
  - 点击多次就会开启多个定时器，这就导致图片的切换速度过快
  - 并且我们只能关闭最后一次开启的定时器
  - 所以我们可以在开启定时器之前，将上一个定时器关闭
```
clearInterval(timer);
/*
  开启一个定时器，来自动切换图片
*/
timer = setInterval(function () {},1000);
```
### 38.3 修改div移动练习
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>使div可以根据不同的方向键向不同的方向移动</title>
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
        }
    </style>
    <script>
        //使div可以根据不同的方向键向不同的方向移动
        /*
         按左键，div向左移动 37
         按右键，div向右移动 39
         按上键，div向上移动 38 
         按下键，div向下移动 40
        */
        //在练习24的基础上修改，使移动没有卡顿，效果更加流程
        //把方向和速度分开管理
        window.onload = function () {
            //获取div
            var box1 = document.getElementById("box1");
            //定义移动方向
            var dir;
            //定义一个变量，来表示移动的速度
            var speed = 10;

            var timer;

            timer = setInterval(function () {
                switch (dir) {
                    case 37:
                        //向左移，left值减小
                        box1.style.left = box1.offsetLeft - speed + "px";
                        break;
                    case 39:
                        //向右移，left值增大
                        box1.style.left = box1.offsetLeft + speed + "px";
                        break;
                    case 38:
                        //向上移，top值减小
                        box1.style.top = box1.offsetTop - speed + "px";
                        break;
                    case 40:
                        //向下移，top值增大                       
                        box1.style.top = box1.offsetTop + speed + "px";
                        break;
                }
            }, 100);

            //为document绑定一个按键按下的事件
            document.onkeydown = function (event) {
                event = event || window.event;
                //当用户按了ctrl键以后，速度加快
                if (event.ctrlKey) {
                    speed = 50;
                } else{
                    speed = 10;
                }
                //使dir等于按键的值
                dir = event.keyCode;
            }

            //为document绑定一个按键松开的事件
            document.onkeyup = function (event) {
                //div不再移动
                dir = 0;
            }
        }
    </script>
</head>
<body>
    <div id="box1"></div>
</body>
</html>
```
### 38.4 延时调用
指的是一个函数不马上执行，而是隔一段时间以后再执行，而且只会执行一次。<br/>
延时调用和定时调用的区别：定时调用会执行多次，而延时调用只会执行一次。<br/>
延时调用和定时调用实际上是可以互相代替的，在开发中可以根据自己的需要去选择。<br/>
- `setTimeout()` <br/>
```
var timer = setTimeout(function(){
  console.log(num++);
},3000);
```
- `clearTimeout()`：关闭一个延时调用
```
clearTimeout(timer);
```
### 38.5 定时器的应用
#### 38.5.1 应用一 
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>定时器的应用一：点击按钮，box1向右移动，移动到500像素时停止</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        #box1 {
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
            left: 0;
        }

        #box2 {
            width: 0;
            height: 1000px;
            border: 1px solid black;
            position: absolute;
            left: 500px;
            top: 0;
        }
    </style>
    <script>
        window.onload = function () {
            //获取box1
            var box1 = document.getElementById("box1");
            //获取btn1
            var btn1 = document.getElementById("btn1");
            //设置速度
            var speed = 10;
            //定义一个变量，用来保存定时器的标识
            var timer;
            //为btn1绑定一个单击响应函数
            btn1.onclick = function () {
                clearInterval(timer);
                //开启一个定时器，用来执行动画效果
                timer = setInterval(function () {
                    //每隔0.1s中，box1向右移动
                    // box1.style.left = box1.offsetLeft + speed + "px";
                    // newValue = box1.style.left - "px";

                    //获取box1的原来的left的值
                    var oldValue = parseInt(getStyle(box1, "left"));

                    //在旧值的基础上增加
                    var newValue = oldValue + 1;

                    //判断newValue是否大于500
                    if (newValue > 500) {
                        newValue = 500;
                    }

                    //将新值设置给box1
                    box1.style.left = newValue + "px";

                    //当元素移动到500px时，使其停止执行动画
                    if (newValue === 500) {
                        clearInterval(timer);
                    }
                }, 100);
            }
        }
        function getStyle(obj, name) {
            if (window.getComputedStyle) {
                //正常浏览器的方式，具有getComputedStyle()方法
                return getComputedStyle(obj, null)[name];
            } else {
                //IE8的方式，没有getComputedStyle()方法
                return obj.currentStyle[name];
            }
        }
    </script>
</head>
<body>
    <button id="btn1">点击按钮以后box1向右移动</button>
    <br /><br />
    <div id="box1"></div>
    <div id="box2"></div>
</body>
</html>
```
#### 38.5.2 应用二 
#### 38.5.3 应用三  