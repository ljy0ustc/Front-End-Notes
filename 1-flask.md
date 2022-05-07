```python
from flask import Flask,render_template

app = Flask(__name__)

#创建网站 /show/info 和函数index的对应关系
#以后用户在浏览器上访问/show/info，网站自动执行
@app.route("/show/info")
def index():
    #return "中国联通"
    #return "中<h1>国</h1><span style='color:red;'>联通</span>"
    #Flask 内部会自动打开这个文件夹并读取内容，将内容给用户返回
    #默认：去当前项目目录的templates文件夹中找
    return render_template("index.html")

if __name__ == '__main__':
    #这里可以设置主机和端口号
    app.run()
```

注意：

* 函数返回值的网页，本质就是一个字符串。

* 由于reder_template查找目录是在当前目录中查找templates，所以要把html文件放到`templates`文件夹下。





