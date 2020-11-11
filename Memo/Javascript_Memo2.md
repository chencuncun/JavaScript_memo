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
### 31.4 forEach
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
### 31.5 

