# css

## 1.表单

### 1.1一个表单的例子

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>用户登录</h1>
    <form>
        用户名：<input type="text" name="username"><br>
        密码：<input type="password" name="password"><br>
        <input type="submit" value="登录">
    </form>
</body>
</html>
```

运行结果如下:

![1563002285658](D:\JAVA学习资料\.vscode\就业班笔记\图片\1563002285658.png)

* ``<form>``的相关属性:

| 常用属性 | 作用                              |
| -------- | --------------------------------- |
| action   | 提交给服务器的地址的URL           |
| method   | 提交的方式,两种提交方式:GET或POST |

### 1.2 表单的常用标签

| 表单项     | 控件代码                                                     | 属性                                                         | 备注                                            |
| ---------- | :----------------------------------------------------------- | ------------------------------------------------------------ | ----------------------------------------------- |
| 文本框     | ``<input type = "text" name ="名字" >``<br>![1563002673546](D:\JAVA学习资料\.vscode\就业班笔记\图片\1563002673546.png) | type:指定空间类型<br />name:传递参数的名字<br />value:文本框中默认的值<br />readonly:只读不能修改<br />disabeld:不可用,数据不能提交给服务器<br />placeholder:用于文本框中的提示文字 |                                                 |
| 密码框     | ``<input type="password">``<br />![1563003041946](D:\JAVA学习资料\.vscode\就业班笔记\图片\1563003041946.png) | 属性同上                                                     |                                                 |
| 单选框     | ``<input type="radio" name="gender" value="男" checked="checked">``<br /> |                                                              |                                                 |
| 复选框     | ``<input type="checkbox" name="hobby" value="游泳">``![1563004017571](D:\JAVA学习资料\.vscode\就业班笔记\图片\1563004017571.png) |                                                              |                                                 |
| 下拉列表   | <select><br /><option>选项<option><br /></select>            |                                                              |                                                 |
| 隐藏表单   | ``<input type="hidden" name="id" value="值">``               | 表单不可见                                                   |                                                 |
| 文本域     | <input type="file" name="photo" accept="image/*">            | accept:接受文件的类型<br />*:支持改类型的所有格式            |                                                 |
| 多行文本域 | ``<textarea name="intro" cols="50" rows="5"></textarea>``    | rows:指定行数<br />cols:指定列数                             |                                                 |
| 提交按钮   | ``<input type="submit" value="注册"/>``                      | value:按钮上显示的文字                                       | ==将整个表单提交给服务器==                      |
| 普通按钮   | ``<input type="button" value="按钮"/>````<button>按钮文字</button>`` |                                                              | 在表单中没有具体的开发功能,主要用于后期程序开发 |
| 图片按钮   | ``<input type ="image" src="img/regbtn.jpg">                 | x,y:鼠标点击图片的位置                                       | 具有于submit相同的功能                          |
|            |                                                              |                                                              |                                                 |



