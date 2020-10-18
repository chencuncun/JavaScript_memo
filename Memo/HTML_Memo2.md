# HTML 笔记重点
## 1. 表格
### 1.1 常用表格
在现实生活中，我们经常需要使用表格来表示一些格式化数据：课程表，名单，成绩单... <br/>
同样，在网页中我们也需要使用表格，我们通过`table`标签来创建一个表格 <br/>
- `table`：表格
- `tr`：行
- `td`：单元格
- `rowspan`：纵向合并单元格
- `colspan`：横向合并单元格
```
<table border="1px" width=400px>
    <tr>
        <td>A1</td>
        <td>B1</td>
        <td>C1</td>
        <td>D1</td>
    </tr>
    <tr>
        <td>A2</td>
        <td>B2</td>
        <td>C2</td>
        <!-- rowspan 纵向合并单元格 -->
        <td rowspan="3">D2</td>
    </tr>
    <tr>
        <td>A3</td>
        <td>B3</td>
        <td>C3</td>
    </tr>
    <tr>
        <td>A4</td>
        <!-- colspan 横向合并单元格 -->
        <td colspan="2">B4</td>
    </tr>
</table>
```
### 1.2 长表格
可以将一个表格分成三个部分：<br/>
- `thead` 头部
- `tbody` 主体
- `tfoot` 底部
- `th` 头部的单元格
```
<table border="1px" width=50%>
    <!-- 头部 -->
    <thead>
        <tr>
            <th>日期</th>
            <th>收入</th>
            <th>支出</th>
            <th>合计</th>
        </tr>
    </thead>
    <!-- 主体 -->
    <tbody>
        <tr>
            <td>2020.10.15</td>
            <td>800</td>
            <td>300</td>
            <td>500</td>
        </tr>
        <tr>
            <td>2020.10.15</td>
            <td>800</td>
            <td>300</td>
            <td>500</td>
        </tr>
    </tbody>
    <!-- 底部 -->
    <tfoot>
        <tr>
            <td></td>
            <td></td>
            <td>合计</td>
            <td>--</td>
        </tr>
    </tfoot>    
</table>
```
### 1.3 表格的样式
- `border-spacing: 0px;`：指定边框之间的距离
- `border-collapse：collapse;`：设置边框的合并
- 各行变色 
```
tr:nth-child(2n+1){
    background-color:#bfa;
}
```
- 注意 <br/>
如果表格中没有使用`tbody`而是直接使用`tr`，那么浏览器会自动创建一个`tbody`，并且将`tr`全都放到`tbody`中 <br/>
`tr`不是`table`的子元素
```
tbody > tr:nth-child(2n+1){
    background-color:#bfa;
}
```
默认情况下，元素在`td`中是垂直居中的，可以通过`vertial-align`来修改
  - `vertical-align: bottom;`：底部居中
  - `vertical-align: middle;`：上下左右居中
  - `text-align: center;`：内容居中 
- `display: tabel-cell;`：将元素设置为单元格
```
<head>
    <style>
        .box1{
            width: 300px;
            height: 300px;
            background-color: green;
            /* 将元素设置为单元格td，就可以使用单元格的属性 */
            display: table-cell;
            /* 上下左右居中 */
            vertical-align: middle;
        }
        .box2{
            width: 100px;
            height: 100px;
            background-color: yellow;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <div class="box1">
        <div class="box2"></div>
    </div>
</body>
``` 
## 2. 表单
### 2.1 基本属性
在现实生活中，表单用于提交数据。<br/>
在网页中也可以使用表单，网页中的表单用于将本地的数据提交给远程的服务器 <br/>
使用`form`标签来创建一个表单 <br/>
- `action`：表单要提交的服务器的地址
```
<form action="target.html">
    <!-- 文本框：数据提交到服务器中，必须要为元素指定一个name -->
    文本框 <input type="text" name="username">
    
    <!-- 密码框：与文本框一样，必须要为元素指定一个name -->
    密码框 <input type="password" name="password">
    
    <!-- 提交按钮，value表示按钮内的名字 -->
    <input type="submit" value="登录">

    <!-- 单选按钮：name属性必须保持一致 
        且必须指定一个value属性，value属性最终会作为用户填写的值传递给服务器
        checked：可以将单选按钮设置为默认选中 
    -->
    单选按钮 <input type="radio" name="hello" value="male" checked>
            <input type="radio" name="hello" value="female">

    <!-- 多选框 -->
    多选框 <input type="checkedbox" name="test" value="1">
          <input type="checkedbox" name="test" value="2">
          <input type="checkedbox" name="test" value="3">

    <!-- 下拉列表 selected：默认选中 -->
    <select name="list">
        <option value="i">选项1</option>
        <option selected value="ii">选项2</option>
        <option value="iii">选项3</option>
    </select>
</form>
```
### 2.2 其他属性
- 按钮
```
<!-- 提交按钮 -->
<input type="submit">
<!-- 重置按钮 -->
<input type="reset">
<!-- 普通按钮 -->
<input type="button" value="按钮">
```
```
<button type="submit">提交</button>
<button type="reset">重置</button>
<button type="button">按钮</button>
```
- `autocomplete="off";`：关闭自动补全
```
<!-- 将所有输入框内的数据清除 -->
<form action="target.html" autocomplete="off">

<!-- 将指定的输入框内的数据清除 -->
<input type="text" name="username" autocomplete="off">
```
- `readonly`：将表单项设置为只读，数据会提交 <br/>
`<input type="text" name="username" readonly>`
- `disabled`：将表单项设置为禁用，数据不会提交 <br/>
`<input type="text" name="username" disabled>`
- `autofocus`：设置表单项目自动获取焦点 <br/>
`<input type="text" name="username" autofocus>`
