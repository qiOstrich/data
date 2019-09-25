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

## MTV：
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

app.py中的代码
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

在`manager.py`中调用：

`app.register_blueprint(blueprint=blue)`



### Flask 请求流程

1. 浏览器页面请求到路由 route('路由参数')
2. 执行route视图函数
3. 视图函数和models交互(使用网页传回的参数与models中的database交互)
4. 模型返回数据到视图函数
5. 视图函数渲染模板
6. 模板返回给浏览器网页

流程图：

```
浏览器→route→views→models↓

↑←←template←views←←←←
```

也有捷径，视图不需要数据，直接渲染，即：

```
浏览器→route→views↓

↑←←template←←←
```



### url_for路由参数

```python
type:
    1.sting 
	2.int
	3.float
	4.path
	5.uuid
    
	6.any(用法稍微有特殊)


前5种用法
@blue.route('/attrname/<type:element>/')
def attrname(element):
	#...
	return 

any的用法
@blue.route('/attrname/<any(enum1,enum2,enum3,enum4,……):element>/')
def attrname(element):
    #...
    return
使用any传回的路由参数一定是在any的元组中有的，
像数据库中的枚举enum；
```



### 安装postman

```
unbuntu应用商店有

或者到官网下

配置：https://blog.csdn.net/Shyllin/article/details/80257755
```

### 接受网页数据

请求方式：

修改http方法（请求方式）：在route中添加参数`methods=['post','get',……]`大小写都可

1. 默认接收方式get，options，head
2. post，一般都是使用表单发送
3. put， 修改请求
4. delete，删除请求

```python
例子：
@blue.route('/getrequest/',methods=['post'])
def getrequrest():
	variable1  =  request.form.get('name') #form表单请求
	variable2  =  request.args.get( 'route_element' ) #路由参数后？中的参数
	# 其他请求方式未得其法
	return render_template('request.html',name=variable1,getvariable2=variable2)
```



### 反向解析 ：url_for，得到路由参数

```
返回值：是路径参数
用法：url_for('blueprint_name.route_method_name')
例子：
blue = Blueprint('blueprint_name',__name__)

@blue.route('/')
def main():
	route_url_varilable = url_for('blueprint_name.main') # 得到的结果是 /
	return render_template('main.html')
```



### request

request可以得到的参数，暂时12个。

```
	1）request是一个内置对象
	内置对象：不需要创建就可以直接使用的对象
（2）属性
	1.method      （请求方法）            **
	2.base_url    （去掉get参数的url）	
	3.host_url    （只有主机和端口号的url）	
	4.url         （完整的请求地址）       **
	5.remote_addr （请求的客户端地址）     **
	6.request.args.get('name')
      args  **
           - args
           - get请求参数的包装，args是一个ImmutableMultiDict对象，类字典结构对象
           - 数据存储也是key-value
           - 外层是大列表，列表中的元素是元组，元组中左边是key，右边是value
           - ImmutableMultiDict([('age', '18'), ('age', '19'), ('name', 'zs')])
           
           注意： 一般情况下  get请求方式都是在浏览器的地址栏上显示
                 eg：http：//www.baiduc.com/s?name=zs&age=18
                 获取get请求方式的参数的方式：request.args.get('name')
          
     7.request.form.get('name')
       form   **
           - form
           - 存储结构和args一致
           - 默认是接收post参数
           - 还可以接收 PUT，PATCH参数
           注意：eg：
                    <form action='xxx' method='post'>
                        <input type='text' name='name'>
                     获取post请求方式的参数的方式
	 8.files       (文件上传)	  **
	 9.headers	   (请求头)
	 10.path       (路由中的路径)	 **
	 11.cookies    (请求中的cookie)
	 12.session	   (与request类似  也是一个内置对象  可以直接打印 print（session）)
```



#### request用法实现

```
request.method
request.base_url
request.host_url
request.url
request.remote_addr
request.form.get()
request.args.get()
……
```



### response

```
route方法的返回值

1.字符串
return  'hello'

2. render_template('base.html')
print(type(render_template('base.html'))) # <class 'str' >
return render_template

3.make_response
print(type(make_response('str')))  #< class 'str' >
return make_response('str')

4.redirect
response = redirect(url_for('blueprint_name.view_method'))
return response

5.Response
response = Response('str')
return response
```



### 异常



abort(exception_code)

````
@blue.route('/error_404/')
def error_404():
	abort(404)
	return 'none'
	
@blue.errorhandler(404)
def handler404(exception):
	return '我们将会处理这个问题'
````



### 会话技术 cookie和session

```
1.请求过程Request开始，到Response结束
2.连接都是短连接
3.延长交互的生命周期
4.将关键数据记录下来
5.Cookie是保存在浏览器端/客户端的状态管理技术
6.Session是服务器端的状态管理技术
```



#### cookie

```
Cookie
	1.客户端会话技术
	2.所有数据存储在客户端
	3.以key-value进行数据存储层
	4.服务器不做任何存储
	5.特性
		(1)支持过期时间
			max_age  毫秒
			expries  具体日期
		(2)根据域名进行cookie存储
		(3)不能跨网站（域名）
		(4)不能跨浏览器
		(5)自动携带本网站的所有cookie
	6.cookie是服务器操作客户端的数据
	7.通过Response进行操作
```



```
cookie登陆使用
	设置cookie     response.set_cookie('username',username)
		
	获取cookie     username = request.cookies.get('username','游客')
		
	删除cookie     response.delete_cookie('username')
```

实例：

````
@blue.route('/login/')
def login():
	username = request.args.get('name')
	response = redirec(url_for('blueprint_name.view_method'))
	response.set_cookie('username',username)
	return response
# 生产一个cookie

@blue.route('/welcome/')
def welcome():
	uername = request.cookie.get('ueraname','未命名')
	return render_template('welcome.html',username=username)
# 得到想要的cookie，没有会使用默认值

@blue.route('/logout/')
def logout():
	response = redirec(url_for('blueprint_name.view_method'))
	response.delete_cookie('username')
	return response
#删除cookie

````



#### session

```
Session
	1.服务端会话技术
	2.所有数据存储在服务器中
	3.默认存在服务器的内存中
		- django默认做了数据持久化（存在了数据库中）
	4.存储结构也是key-value形势，键值对
	【注】单纯的使用session是会报错的，需要使用在__init__方法中配置app.config['SECRET_KEY']=‘110’
```



```python
__init__.py:

def create_app():
	app = Flask(__name__)
	
	app.config['secret_key'.upper()]='12306'
	app.config['session_type'.upper()]='redis'
	Session(app=app)
	
    return app
# 使用session一定要设置秘钥，不然会报错
# 将session存储到redis中
```



```
session登陆使用
	设置    session['username'] = username
	获取    session.get('username')
	删除
		   resp.delete_cookie('session')
		   session.pop('username')
```

#### cookie和session总结

```
（1）cookie: 客户端浏览器的缓存；session: 服务端服务器的缓存
（2）cookie不是很安全，别人可以分析存放在本地的cookie并进行cookie欺骗，考虑到安全应当使用session
（3）session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能，考虑到减轻服务器性能方面，应当使用cookie
可以考虑将登陆信息等重要信息存放为session，其他信息如果需要保留，可以放在cookie中
```



#### session持久化

cookie和session默认是在内存中存储的，不能永久使用，持久化就是实现cookie和session存储在数据库中。

1. django中对session做了持久化，存储在数据库中
2. flask中没有对默认session进行任何处理
       - flask-session 可以实现session的数据持久化
           - 可以持久化到各种位置，更推荐使用redis
           - 缓存在磁盘上的时候，管理磁盘文件使用lru, 最近最少使用原则



实现持久化：

```
	1.pip install flask-session
			在国内源安装
			pip install flask-sessin -i https://pipy.douban.com/simple 
			# 使用豆瓣服务器下载
	2.初始化Session对象 
			（1）持久化的位置
				配置init中app.config['SESSION_TYPE'] = 'redis'
				后面将会在ext.py中封装到函数中
				
			（2）初始化
				创建session的对象有2中方式 分别是以下两种
				在ext.py中，写在config配置下面才能是配置应用
				1 Session(app=app)
				2 se = Session()   se.init_app(app = app)
				
			（3）安装redis   
				pip install redis
				
			 (4)需要配置SECRET_KEY='110'
			 	注意：flask把session的key存储在客户端的cookie中，通过这个key可以从flask的内存中获取					 用户的session信息，出于安全性考虑，使用secret_key进行加密处理。所以需要先设置secret_key的值。
			 	
			（5）其他配置--视情况而定
				app.config['SESSION_KEY_PREFIX']='flask'
				#在redis存储中，会加上这个前缀
		
     特殊说明：
            查看redis内容
                    redis-cli
                    keys *
                    get key
            session生存时间31天	
                ttl session
                    flask的session的生存时间是31天，django的session生存时间是15天
```



### template

```
temlates文件夹 
存放模板(html)的文件夹，可以通过app=Flask(__name__,static_folder=绝对路径,template_folder=绝对路径)
```

```
	（1）MVC中的View，MTV中的Template
	（2）主要用来做数据展示的
	（3）模板处理过程分为2个阶段
            1 加载
            2 渲染
    （4）jinja2模板引擎
            1.本质上是html
            2.支持特定的模板语法
            3.flask作者开发的   一个现代化设计和友好的python模板语言  模仿的django的模板引擎
            4.优点
                    速度快，被广泛使用
                    HTML设计和后端Python分离
                    减少Python复杂度
                    非常灵活，快速和安全
                    提供了控制，继承等高级功能

```

模板语法：

基本语法

```
模板语言动态生成的html
		{{ var }}  变量的接收
			从views传递过来的数据
			前面定义出来的数据
			
在视图函数中使用render_template('test.html',var=variable)
# 其中var是html中接受变量的参数，variable是视图函数中的数据
```

结构标签

```
（1）block
        首次出现挖坑操作
        第二次出现填坑操作
        第N次出现，填坑操作，会覆盖前面填的坑
        不想被覆盖，需要添加 {{ super() }}
（2）extends
	    继承
（3）include
		包含，将一个指定的模板包含进来

示例：
{% extends 'base.html' %}

{% include 'addin.html' %}

{% block header %}
{% endblock %}
```

宏定义

```
无参
{% macro say() %}
内容、操作。
{% endmacro %}

调用：
{{ say() }}

有参
{% macro say(dog) %}
小狗狗才这么叫：{{ dog }}
{%  endmacro %}

导入外文件的宏定义

{%  from 'base.html' import say(dog) %}
{{ say('汪汪汪') }}
```



循环控制器

```
{% for i in songs %}
 歌曲名：{{ i.song }}
 作曲者：{{ i.singer }}
 {% endfor %}
 
 {% if 条件式 %}
 执行语句1
 {% elif 条件式 %}
 执行语句2
 {% else %}
 执行语句3
 {% endif %}
 
```

过滤器 |

```
语法格式：{{ var|xxx|yyy|zzz }}
没有数量限制
		lower   字符串小写
		upper   字符串大写
		trim       去除头尾空格
		reverse 逆序
		striptags   渲染之前将值中的标签去掉
		safe        标签生效
		eg:
			{% for c in config %}
                    <li>{{ loop.index0 }}:{{ loop.index}}:{{ c|lower|reverse }}</li>
    		{% endfor %}
```



### models

```
1.数据交互的封装
2.Flask默认并没有提供任何数据库操作的API
	Flask中可以自己的选择数据，用原生语句实现功能
		原生SQL缺点:
              （1）代码利用率低，条件复杂代码语句越过长，有很多相似语句
              （2）一些SQL是在业务逻辑中拼出来的，修改需要了解业务逻辑
              直接写SQL容易忽视SQL问题
	也可以选择ORM
		SQLAlchemy
		MongoEngine
		将对象的操作转换为原生SQL
		优点
			 （1）易用性，可以有效减少重复SQL
              （2）性能损耗少
              （3）设计灵活，可以轻松实现复杂查询
              （4）移植性好
3.Flask中并没有提供默认ORM
	ORM 对象关系映射
	通过操作对象，实现对数据的操作
```

### sqlalchemy

```
flask-sqlalchemy
     使用步骤：1.pip install flask-sqlalchemy
              2.创建SQLALCHEMY对象
                                   ①：db=SQLAlchemy(app=app)
                                   ②：db=SQLAlchemy()  上面这句话一般会放到models中  因为需要db来调                                       用属性 db.init_app(app=app)
              3.config中配置  SQLALCHEMY_DATABASE_URI
                                    数据库 + 驱动 :// 用户:密码@ 主机:端口/数据库
                                    dialect+driver://username:password@host:port/database
                                    eg:mysql+pymysql://root:1234@localhost:3306/flask1905
              4.执行
                    views中db.create_all()
                    
              注意：有坑
                            （1）primary-key
                                添加主键
                            （2）SQLALCHEMY_TRAKE_MODIFICATIONS
                                	app.config[‘SQLALCHEMY_TRAKE_MODIFICATIONS’]=False         

关于数据库的配置，可以在settings中创建类，因为app.config.from_object(ConfigClass)可以得到类的属性
settings.py:
class Config():
	SQLACHEMY_TRAKE_MODIFICTIONS =False 
	Test = False
	Debug = False
	
class DevelopConfig(Config):
	DATABASE={
		'dialect':'mysql',
		'driver':'pymysql',
		'user':'qmc',
		'passwd':'123',
		'host':'localhost',
		'port':'3306',
		'database':'exercise',
	}
	SQLALCHEMY_DATABASE_URI=get_uri(DATABASE)

def get_uri(database):
	return "{dialect}+{driver}://{user}:{passwd}@{host}:{port}/{database}".format(**database)
ENVIRO={
	'develop':DevelopConfig,
	'test':TestConfig,
	'show':ShowConfig,
	'production':ProduntionConfig,
}

__init__.py:

app.config.from_object(settings.ENVIRO.get(env.lower()))
db.init_app(app=app)
```



```
models.py:

db =SQLAchemy()

class Student(db.Model):
	__tablename__='student'
	id = db.Column(db.Integer,primary_key=True,autoincrement=True)
	name =db.Column(db.String(32))
	
	
视图函数中使用：
db.create_all() # 创建表

db.drop_all() # 删除表

添加数据:

db.session.add(student1)  #其中student1是Student类的对象
de.session.commit() # 调教添加才会在数据库产生作用

Student.query.all() # 得到所有的数据，返回值是basequery对象
可以使用下标索引得到basequery中的对象
```



### 项目拆分

```
一个项目需要4个环境，最少也要3个：
	（1）开发环境
                开发环境
                测试环境
                演示环境-类似线上环境也叫做预生产环境 可以使用测试环境代替
                线上环境 也叫做 生产环境
	（2）拆分项目
                规划项目结构
                    manager.py
                        app的创建
                        Manager （flask-script管理对象）
                    App
                        __init__
                            创建Flask对象
                            加载settings文件
                            调用init_ext方法
                            调用init_blue方法
                        settings
                            App运行的环境配置
                            运行环境
                        ext（扩展的，额外的）
                            用来初始化第三方的各种插件
                            Sqlalchemy对象初始化 数据库
                            Session初始化
                        views
                            蓝图
                            创建
                            注册到app上
                        models
                            定义模型
```



### flask-migrate

```
使用前需要安装：
pip install flask-migrate

初始化：
在ext.py:
migrate =Migrate()
migrate.init_app(app=app,db=db)

manager.py:
manager.add_command('db',MigrateCommand)

命令行执行:
python manager.py db init  #初始化
python manager.py db migrate #生成迁移文件 bug原因，模型定义完成从未调用（未产生表）；数据库已经有模型记录
python manager.py db upgrade # 升级
python manager.py db downgrade # 降级
```

### DML

##### 增

```
增
db.session.add(模型对象)
db.session.commit()# 提交

student_list=[student1,student2,……]
db.session.add_all(student_lsit)
db.session.commit()
```

##### 删

```
删
一般需要先查找到对象：
student =Student.query.first()
db.session.delete(student)
db.session.commit()
```

##### 改

```
改
一般需要先查找到对象：
student = Studet.query.first()
student.name ='辗迟'
db.session.add(student)
db.session.commit()
```

##### 查

```
查单个数据
student = Student.query.get(1)
# 默认查找主键，得不到不会报错
student = Student.query.first()
#找到数据库中第一个数据
```

```
查多个数据，无论是否找到返回basequery
student = Student.query.all() 
# 得到所有数据
student = Student.query.filter_by(name='辗迟')
# 得到所有name='辗迟'的对象，在basequery中
student = Student.query.filter(Student.name == '辗迟')
# 也是得到所有Student.name == '辗迟' 的对象，返回值也是basequery
student = Student.query.filter(Student.id> 2)
# 得到id字段大于2的所有对象 
# 小于同理
 student = Student.query.filter(Student.id.__le__(2))
 # 得到id小于等于2的所有对象
 # 大于等于同理
persons = Person.query.filter(Person.p_name.startswith("小"))
# 得到所有name字段以'小'开头的对象
persons = Person.query.filter(Person.p_name.endswith("1"))
# 得到所有name字段以'大'开头的对象
persons = Person.query.filter(Person.p_name.contains("1"))
#得到所有name字段包含'1'的对象
persons = Person.query.filter(Person.p_age.in_([15, 11]))
# 得到age为 15,11的对象
```

##### 数据筛选

````
数据筛选
	（1）order_by
			升序：
				persons = Person.query.order_by("p_age")
			降序：
				persons = Person.query.order_by(db.desc('p_age'))
	（2）limit
			persons = Person.query.limit(5)
	（3）offset
			persons = Person.query.offset(5).order_by("id")
	（4）offset和limit不区分顺序，offset先生效
			persons = Person.query.order_by("id").limit(5).offset(5)
			persons = Person.query.order_by("id").limit(5)
		 	persons = Person.query.order_by("id").offset(17).limit(5)
	（5）order_by 需要先调用执行(order_by无论在语法还是执行顺序都是先执行)
		 	persons = Person.query.order_by("id").offset(17).limit(5)
````

有order_by一定要放在最前面！！！

##### 分页

```
在flask-sqlalchemy中已经分装好了pagination类供使用：
paginate =Student.query.paginate(page=page,per_page=per_page)
得到的是一个pagination对象
他有属性：
items   遍历参数，迭代得到页中的对象
prev_num # 上一页页码（底层实现自减1）
next_num # 下一页页码（底层实现自增1）
has_prev   # 是否有上一页
has_next   # 是否有下一页
pages         # 总页数
iter_pages # 总页数迭代对象
```

##### 逻辑运算

```
	（1）与
		    and_     filter(and_(条件))
			huochelist = kaihuoche.query.filter(and_(kaihuoche.id == 1,kaihuoche.name == 'lc'))

	（2）或
			or_          filter(or_(条件))
			huochelist = kaihuoche.query.filter(or_(kaihuoche.id == 1,kaihuoche.name =='lc'))

	（3）非
			not_         filter(not_(条件))  注意条件只能有一个,导包注意是sqlalchemy的包
			huochelist = kaihuoche.query.filter(not_(kaihuoche.id == 1))

	（4）in
		    huochelist = kaihuoche.query.filter(kaihuoche.id.in_([1,2,4]))
```

因为python的底层源码短路问题not_需要导入sqlalchemy的包



##### 数据类型及参数

```
	（1）字段类型
                Integer
                String
                Date
                Boolean
	（2）约束
		primary_key   （主键）   			
		autoincrement （主键自增长）     			
		unique        （唯一） 			
		default       （默认）   			
		index         （索引）    			
		no't'null     （非空）			
		ForeignKey    （外键）                       
                        用来约束级联数据
                        db.Column( db.Integer, db.ForeignKey(xxx.id) )
                        使用relationship实现级联数据获取
                            声明级联数据
                            backref="表名"
                            lazy=True
```



##### 模型关系

一对一

一对多，多对一

多对多



使用外键关联：

````
（1）模型定义
          class Parent(db.Model):
              id=db.Column(db.Integer,primary_key=True,autoincrement=True)
              name=db.Column(db.String(30),unique=True)
              children=db.relationship("Child",backref="parent",lazy=True)


          class Child(db.Model):
              id = db.Column(db.Integer, primary_key=True)
              name = db.Column(db.String(30), unique=True)
              parent_id = db.Column(db.Integer, db.ForeignKey('parent.id'))
# db.ForeignKey('parent.id')外键说明，关联parent的id字段
其中relationship表示建立关联，backref 表示反向关联，lazy=True表示select 属于懒查询，需要使用数据的时候才会查找，而不会立即执行
````

### flask-bootstrap

```
使用前先安装：
pip install flask-bootstrap

在ext.py加入：
Bootstrap(app =app)
导入这个包可以使用其中定义好的模板
 {% extends ‘bootstrap/base.html’%}
```

### 缓存flask-cache

```
使用前安装：
pip install flask-cache

目的：通过缓存的形式达到快速查找的目的，而不是直接在大量数据库中查找

实现方案：
          （1）数据库
          （2）文件
          （3）内存
          （4）内存中的数据库 Redis
实现流程
          （1）从路由函数进入程序
          （2）路由函数到视图函数
          （3）视图函数去缓存中查找
          （4）缓存中找到，直接进行数据返回
          （5）如果没找到，去数据库中查找
          （6）查找到之后，添加到缓存中
          （7）返回到页面上
          
首先初始化：
ext.py：
全局变量：
cache=Cache(config={'CACHE_TYPE':'redis'}) 其中cache_type默认是simple
cache = Cache(config={'CACHE_KEY_PREFIX':'python'})
在扩展初始化app函数中：
cache.init_app(app=app)
```

使用方式：

```
在视图函数的route路径下增加一个装饰器：
@cache.cached(timeout=30)
例子：
@blue.route('/testcache/')
@cache.cached(timeout=30)
def testCache():
	执行语句
	return 'YES'
	
第一次执行这个视图函数之后会将结果存在缓存中，30秒之内再次调用不会执行这个视图函数而直接得到缓存中的结果

原生代码实现缓存：

cache.set('ip',ip) 设置缓存保留的值是ip 取名为'ip'
chache.get('ip'),尝试得到缓存中的ip值，没有就没有了
```

### 钩子

```
@before_request
def aop():
	# 连接数据库，等操作

定义了钩子函数，那么在每次执行视图函数之前都会自动执行钩子函数。而不需要再次调用这个钩子函数
```

### 四大内置对象

1. request，得到请求信息，

```
methods 请求方式，http方法
base_url
host_url
url
remote_addr   请求地址
path
headers
file
cookie
session
form
args
```



2. session

```
服务端会话技术：
session['sesion_name']=sesion_name # 设置一个session_key

session.get('session_name') #尝试得到一个session_key

session.pop('session_name')
response.delete_cookie('session_name')
#以上两句都是删除session
```

3. config

```
配置
可以在模板中直接使用config得到配置
可以在python代码中使用current_app.config 的到配置

模板中：
{% for foo in config %}
        <li>{{ foo }}</li>
 {% endfor %}
 python代码：
 n = current_app.config
    print(n)
```

4. g

```
加在变量前面表示全局的变量。
例子：
@blue.route('/testG/')
def testG():
	g.ip = request.remote_addr
	return '定义了一个全局ip'

@blue.route('/getG/')
def getG():
	print(g.ip)
	return '我得到了它'

```



### 文件绝对路径与修改static和templates文件夹位置

```
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

init中app = Flask（__name__,static_folder=static_folder）

static_folder=os.path.join(settings.BASE_DIR,'static')
```

### 前后端分离

通过判断前端的请求方式（http方法）来在同一个路径下进行不同的操作

```
整合网络和软件的一种架构模式
理解
	Representtational
		表现层
	State Transfer
		状态转换
	表现层状态转换
		资源（Resource）
	每一个URI代表一类资源
		对整个数据的操作
		增删改查
RESTful中更推荐使用HTTP的请求谓词（动词）来作为动作标识
	GET
	POST
	PUT
	DELETE
	PATCH
推荐使用json数据传输 
使用jsonify（数据）进行数据类型的转换，得到一个response对象

```

例子：

```
@blue.route('/testSplit/',method=['get','post','put','patch','delete'])
def testSplit():
	if request.method == 'GET': # 请求方式一定要大写
		return 'get请求'
	elif request.method == 'POST':
		return 'post请求'
	elif request.method == 'PUT':
		return 'put请求'
	elif request.method == 'PATCH':
		return 'patch请求'
	elif request.method == 'DELETE':
		return 'delete请求'
	return 'something wrong'
```

### flask-restful

框架简化

不适用视图函数，不创建views.py文件

创建一个apis文件夹

```
使用前安装
pip install flask-restful

创建一个urls.py文件，定义一个函数init_urls
初始化，在init中调用itit_urls
			api = Api()
			api.add_resource(Hello, "/hello/")
				Hello是一个类的名字  hello是路由
			def init_urls(app):
    		api.init_app(app=app)
    		
    		
    		apis--基本用法
		继承自Resource
			class Hello(Resource):
		实现请求方法对应函数
			def get(self):
        		return {"msg": "ok"}

            def post(self):
                return {"msg": "create success"}
```

改变：

views.py文件删除，

migrations文件夹删除，使用时重新初始化

manager.py 删除蓝图

models.py 类删除，使用时重新写

\__init__.py中调用init_urls(app)函数

urls.py 新创建 -创建api对象

```
api = Api()

def init_urls(app):
	api.init_app(app=app)
	
api.add_resource(CatResource,'/cat/')
api.add_resource(DogResource,'/dog/')
api.add_resource(PigResource,'/pig/')
api.add_resource(FoxResource,'/fox/')
api.add_resource(PandaResource,'/panda/')
# CatResource导入自apis中的Catapis.py
```

apis 新建文件夹

#### 输出

其中CatApis.py

```
Catapis.py:

class CatResource(Resource):
	def get(self):
		data={
			'msg':'get',
			'status':200,
		}
		return data
		
		def post(self):
		data={
			'msg':'post',
			'status':200,
		}
		return data
		put，patch，delete同理创建函数
```

其中DogApis.py

```
DogApis.py:

class DogResource(Resource):
	
	r1Fileds={
		'msg':fields.String(default='OK'),# 设置了一个默认值
		'status':fields.Integer,
		'msg1':fields.String,
		'msg2':fields.String(attribute='c'),
		
	}
	
	@marsh_with(r1Fileds)
	def get(self):
		data={
			'msg':'get',
			'status':200,
			'a':'b', # 结构中没有不会传递，会被过滤掉
			'c':'d'# c会被更名为msg
		}
		
		return data
```

```
PigApis.py:


r1Fileds={
		'msg':fields.String(default='OK'),# 设置了一个默认值
		'status':fields.Integer,
		'msg1':fields.String,
		'msg2':fields.String(attribute='c'),
	}
class PigResource(Resource):
	

	
	
	def get(self):
		data={
			'msg':'get',
			'status':200,
			'a':'b', # 结构中没有不会传递，会被过滤掉
			'c':'d'# c会被更名为msg
		}
		
		return marshal(data=data,fields=r1fields)
```

Nested(嵌套)使用：传对象

```
FoxApis.py:

class FoxResouce(Resource):

	r2field = {
		'id':fields.Integer,
		'name':fields.String,
	}
	r1field ={
		'msg':'OK',
		'status':fields.Integer,
		'fox':fields.Nested(r2field)
	}
	@marshal_with(r1field)
	def get(self):
		fox = Animal.query.first()
		data={
			'msg':'OK',
			'status':200,
			'fox':fox,
		}
		return data

```

List(列表)使用：传列表

```
PandaApis.py:

class PandaResouce(Resource):

	r2field = {
		'id':fields.Integer,
		'name':fields.String,
	}
	r1field ={
		'msg':'OK',
		'status':fields.Integer,
		'fox':fields.List(fields.Nested(r2field))
	}
	@marshal_with(r1field)
	def get(self):
		pandas = Animal.query.all()
		data={
			'msg':'OK',
			'status':200,
			'fox':pandas,
		}
		return data

```



#### 输入

```
parser =reqparse.Requset()
TigerApis.py:

class TigerResouce(Resource):

	r2field = {
		'id':fields.Integer,
		'name':fields.String,
	}
	r1field ={
		'msg':'OK',
		'status':fields.Integer,
		'fox':fields.List(fields.Nested(r2field))
	}
	@marshal_with(r1field)
	def get(self):
		tigers = Animal.query.all()
		data={
			'msg':'OK',
			'status':200,
			'fox':pandas,
		}
		return data

```









### flask-restful返回中文：加一句

app.config.update(RESTFUL_JSON=dict(ensure_ascii=False))















