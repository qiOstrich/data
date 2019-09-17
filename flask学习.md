# flask学习

## 官方文档：
	http://flask.pocoo.org/docs/0.12/      英文
	http://docs.jinkan.org/docs/flask/    
    中文
### 简介
Django是使用python封装的重量级框架，需要用到的功能都已经被封装好了
flask 是使用python封装的轻量级框架，自由灵活，高度定制。使用简单的核心，用extension增加其他功能
flask 以前有三个依赖库，现在已经增加到了6个
其中jinja2（模板引擎）和Werkzeug（WSGI工具集）是重点。Itsdangerous（基于Django的签名模块）

flask是当前市场上流行的框架之一，其流行的原因有4：
1.  有非常齐全的官方文档，上手非常方便。
2.  有非常好的扩展机制和第三方扩展环境，工作中常见的软件都会有对应的扩展，动手实现扩展也很容易。
3.  社区非常活跃 热度极高（原因在于众多的扩展包，随着扩展包的更新，flask也需要相应的更新）
4.  微型框架的形式给了开发者更大的选择空间

### BS/CS
概念：
browser/server 浏览器/服务器  已经成为主流
client/server 客户端/服务器  
B/S结构是web兴起后的一种网络结构模型，web浏览器是客户端最主要的应用软件。这种模式统一了客户端，将系统功能实现的核心部分集中到服务器上，简化了系统的开发、维护和使用。
随着Html5的出现，web能够实现的功能越来越多，这也方便了用户使用（不需要事先下载客户端），打开浏览器就可以使用。
C/S结构需要先下载客户端，使用本地客户端连接服务器，对于新用户来说较为繁琐。
优点：可以在局域网内使用，对于权限有多层的检验，安全性也较高些。
缺点：需要相同的操作系统，对于计算机的硬件有一定要求，使用之前需要先安装，需要进行维护（打补丁）
#### cs和bs的对比：
| 对象|硬件环境|客户端要求|软件安装|升级和维护|安全性|
|:|:|:|:|:|
|C/S|用户固定，要求处于相同区域，要求拥有相同的操作系统|客户端的计算机电脑配置要求较高|每一个客户端都必须安装和配置软件|C/S每一个客户端都要升级程序。可以采用自动升级。|一般面对想相对固定的用户群，程序更加注重流程，可以对权限进行多层次校验，提供了更安全的存取模式，对信息安全的的控制能力很强（抓包需要专用的软件）。一般高度机密的信息系统采用C/S结构适宜。|
|B/S|要有操作系统和浏览器，与操作系统平台无关。|客户端的见算计电脑配置要求较低|可以再任何地方进行操作而不用安装任何专门的软件（使用自带的浏览器）|不必安装及维护|在进行TCP报文传递的时候可以轻易的获取包内的信息，安全性较低|

## MVC
MVC：软件架构思想
	简介：
		MVC开始是存在于桌面程序中的，M是指业务模型 model，V是指用户界面 view，C则是控制器 controler，使用MVC的目的是将M和V的实现代码分离，从而使同一个程序可以使用不同的表现形式。比如一批统计数据可以分别用柱状图、饼图来表示。C存在的目的则是确保M和V的同步，一旦M改变，V应该同步更新
实现了模型层的复用。

核心思想: 
	解耦合
面向对象语言：高内聚  低耦合
Model
	模型
	封装数据的交互操
		CRU
View
	视图
	是用来将数据呈现给用户
Controlle
	控制
	接受协调Model和View的关系，并对数行作，筛选
流程
	控制器接受用户请求
	调用模型，获取数据
	控制器将数据展示到视图中

### MTV：
MTV也叫做MVT
本质上就是MVC，变种
Model
	同MVC中Model
Template
	模板
	只是一个html，充当的是MVC中View的角色，用来做数据展示
Views
	视图函数
	相当于MVC中Controller

## flask的基本使用

flask使用前的准备工作
```
pip install virtualenv 
# 下载虚拟环境包
# 创建虚拟环境
virtualenv  ~/.virtualenv_name # 
# 使用ubuntu终端命令创建一个虚拟环境文件夹。名字自已定义（因为虚拟环境文件夹中的文件不必手动更改，所以可以创建隐藏文件）

source ~/.virtualenv/bin/activate
#进入虚拟环境中
pip freeze 
pip list 
# 以上的两个命令查看虚拟环境中的python第三方包，新建的虚拟环境没有第三方包

pip freeze > requirments.txt
# 将python的第三方包名字及版本导出到 requirments.txt 
pip install -r requirments.txt
# 通过文件下载包
```

flask 项目的创建
```
pip install flask -i https://pypi.douban.com/simple
通过url中的服务器下载flask

mkdir python_code
# 存放python代码的文件夹
vim sep17_first_flask.py

```

sep17_first_flask.py中的代码
```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def main():
    return 'hello'

if __name__ == "__main__":
    app.run(host='127.0.0.0',port=8888,debug=True)

```
这是最简单的flask网页
在终端中给予了执行权限后就可以运行
python sep17_first_flask.py

在网页中访问127.0.0.1:8888/
网页中就会出现hello

run中的参数：
`host：主机号`
`port：端口号`
`debug：修改python中的代码后，服务器自行重启`
`threaded：开启多线程（一般不需要设置）`

扩展：PIN码
全程：Personal Identification Number 是一种SIM卡上的个人识别密码，一般在重启或SIM转移后验证，3次错误后锁定SIM卡，这时就需要PUK码解锁。PUK码需要通过客服才能获得

命令行修改端口：
```
pip install flask-script
# 下载扩展包

from flask import Flask
from flask_script import Manager
app = Flask(__name__)

@app.route('/')
def main():
    return '人间不值得'

manager = Manager(app=app)

if __name__ == "__main__":
    manager.run()

```
终端命令:
mv sep17_first_flask.py manager.py

python manager.py runserver -p 8888 -d -r
启动flask网站

命令行参数：
```
-p 8888        port,端口号
-h '0.0.0.0'  host,主机号
-d                   debug
-r                    restart
```

对于@app.route()修饰函数的返回值：
不能返回整形。
可以返回字符串，元组……等数据类型

代码分层：
-App
-   -static --资源文件
-   -templates --模板文件html
-   -__init__.py
-   -views.py
-   -models.py
-manager.py

__init__.py中的代码：
```
from flask import Flask()
from App.views import blue

def create_app():
    app = Flask(__name__)
    app.register_blueprint(blueprint=blue)
    return app
```

manager.py中的代码：
```
from flask_script import Manager

app=create_app()
manager=Manager(app=app)

if __name__ == "__main__":
    manager.run()
```

views.py中的代码：
```
from flask_blueprint import Blueprint
from flask import render_template

blue =Blueprint('name',__name__)

@blue.route('/')
def main():
    return 'hello'

@blue.route('/testrender')
def testrender():
    s = render_template('testrender.html')
    return  s
    
```

templates文件夹中需要有一个名为testrender.html的网页文件

其中blue的定义需要引入第三方包
`pip install flask-blueprint`
初始化语句：
`blue = Blueprint('blueprint_name',__name__)`
初始化语句一定要在views.py中
在manager.py中调用：
app.register_blueprint(blueprint=blue)



