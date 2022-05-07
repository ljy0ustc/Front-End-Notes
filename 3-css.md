## style

1. ```css
   <div style="color:red;">中国联通</div>
   ```

2. ```css
   /*写在head标签中,定义style，方便复用*/
   <head>
   	<meta charset="UTF-8">
   	<title>Title</title>
   	<style>
   		/* .与class关联（类选择器）*/
   		.c1{
   			color:red;
   		}
   		/* #与id关联（id选择器）*/
           #c2{
               color:red;
           }
   		/* 某种标签（标签选择器）*/
           li{
               color:pink;
           }
   		/* 属性选择器 */
   		input[type='text']{
       		border: 1px solid red;
   		}
   		/* 后代选择器 先根据class名找到那个标签，然后给它后代赋予该style */
   		.yy li{
       		color:red;
   		}
   	</style>
   </head>
   /* 应用的时候 class='...' */
   <h1 class='c1'>用户登录</h1>
   ```

3. ```css
   写在文件中,类似于导入
   <head>
   	<meta charset="UTF-8">
   	<title>Title</title>
   	<link rel="stylesheet" href="/static/common.css">
   </head>
   应用的时候 class='...'
   <h1 class='c1'>用户登录</h1>
   ```



补充，同时应用两个class：

* 下面的class覆盖上面的class

* 加上! important可以防止被覆盖

```css
<div class="c1 c2">中国联通</div>
```



## 样式

##### 1. 高度和宽度

* 宽度支持百分比，高度不支持
* 对行内标签默认无效，对块级标签默认有效（右侧区域即使空白也不给占用）

```css
.c1{
	height: 300px;
	width: 500px;
	}
.c1{
	height: 30%;
	width: 500px;
	}
```

##### 2.块级和行内标签

```css
.c1{
	display:inline-block;
	height: 300px;
	width: 500px;
	}
```

##### 字体大小颜色位置

```css
.c1{
	color:#00FF7F;
	font-size:58px;
	font-weight:100;
    font-family:............
    text-align:center;/*水平方向居中*/
    line-height:59px;/*垂直方向居中*/
	}
```

