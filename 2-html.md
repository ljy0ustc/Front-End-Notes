## head

配置和引用

```html
<head>
	#编码
	<meta charset="UTF-8">
    #浏览器能识别的标签
    <title>我的联通</title>
</head>
```



## Body

### 标题

```html
<h1>1级标题</h1>
<h2>2级标题</h2>
<h3>3级标题</h3>
<h4>4级标题</h4>
<h5>5级标题</h5>
<h6>6级标题</h6>
```

### div span 跳转

```html
#一个div占一整行(块级标签)
<div>中国</div>
#span自己多大占多少(行内标签、内联标签)
<span>成都</span>
#a，超链接
# 跳转到别人的网站
<a href="http://www.baidu.com">点击跳转</a>
# 跳转到自己的网站 
<a href="/get/news">点击跳转</a>
#在新的tab页面打开
<a href="http://www.baidu.com" target="_blank">点击跳转</a>
```

### 图片

```html
<img src="图片地址"  style="height:100px;width:100px;"/>
<img src="图片地址"  style="height:10%;width:10%;"/>
#显示自己的图片，要放在static目录
#显示网络上别人的图片放链接就行，可能有防盗链
#可指定高度宽度
```

### 列表

```html
<ul>
	<li>中国移动</li>
	<li>中国联通</li>
	<li>中国电信</li>
</ul>
<ol>
	<li>中国移动</li>
	<li>中国联通</li>
	<li>中国电信</li>
</ol>
```

### 表格

```html
<table>
	<thead>
		<tr> <th>ID</th> <th>name</th> <th>age</th> </tr>
	</thead>
	<tbody>
		<tr> <td>123</td> <td>liao</td> <td>20</td> </tr>
        <tr> <td>123</td> <td>liao</td> <td>20</td> </tr>
        <tr> <td>123</td> <td>liao</td> <td>20</td> </tr>
        <tr> <td>123</td> <td>liao</td> <td>20</td> </tr>
	</tbody>
</table>
```

### input

```html
#输入文字
<input type="text">
#输入密码
<input type="password">
#选择文件
<input type="file">
#单选框
<input type="radio" name="n1" value="1">男
<input type="radio" name="n1" value="2">女
#复选框
<input type="checkbox" name="hobby" value="10">篮球
<input type="checkbox" name="hobby" value="20">棒球
<input type="checkbox" name="hobby" value="30">乒乓球
<input type="checkbox" name="hobby" value="40">足球
#普通按钮
<input type="button" value="提交">
#提交表单
<input type="submit" value="提交">
```

### 下拉框

```html
#单选下拉框
<select>
	<option>北京</option>
    <option>上海</option>
    <option>深圳</option>
</select>
#多选下拉框
<select name="city" multiple>
	<option value="bj">北京</option>
    <option value="sh">上海</option>
    <option value="sz">深圳</option>
</select>
```

### 多行文本

```html
#输入多行文本，可限定高度
<textarea rows="3"></textarea>
```



## 网络请求

在浏览器的URL中写入地址点击回车，访问。

它会发送数据给后端，本质上发送的是字符串。

* GET请求【URL方法/表单提交】
  * get请求、跳转、向后台传入数据会***拼接在URL上***
* POST请求【表单提交】
  * 提交数据不在URL中体现而是在请求体中

用`<form></form>`来包裹提交数据，指定`method="get" action="提交的地址"`

```html
# GET请求跳转的URL会包含uu和pp的值
# /xxx/xxx/xx?uu=wupeiqi&pp=123
<form method="get" action="/xxx/xxx/xx">
	用户名:<input type="text" name="uu">
    密码:<input type="password" name="pp">
    <input type="submit" value="submit按钮">
</form>
```

页面数据要提交到后台：

* 必须要用form包裹要提交数据的标签
  * 提交方式 ：如`method="get"`
  * 提交的地址：如`action="/xxx/xxx/xx"`
  * 在form标签里面必须要有submit

* 在form里面的标签：input/textarea/

  * 一定要赋予name 

* GET形式绑定URL：

  ```python
  @app.route("get/reg",methods=["GET"])
  def do_register():
  	# 1. 接收用户发过来的数据
      print(request.args)
      # 2. 给用户返回结果
      return "注册成功"
  ```

* POST形式绑定URL：

  ```python
  @app.route("post/reg",methods=["POST"])
  def do_register():
  	# 1. 接收用户发过来的数据
      user=request.form.get("user")
      pwd=request.form.get("pwd")
      gender=request.form.get("gender")
      #多选要getlist
      hobby_list=request.form.getlist("hobby")
      # 2. 给用户返回结果
      return "注册成功"
  ```

* 可以将两种形式写在一起

  ```python
  @app.route("post/reg",methods=["POST","GET"])
  def do_register():
  	if request.method=="GET": # GET
  		return ..
  	else: # POST
  		return ..
  ```

  