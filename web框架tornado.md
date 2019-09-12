# web框架之tornado

HTTP协议是建立在TCP协议之上的短连接协议。

HTTP采用了TCP的可靠性，保证了数据的完整。

socket建立一个简单的HTTP Server

```python
import socket

ADDR = ('0.0.0.0', 80)
RESPONSE = b'''
HTTP/1.1 200 OK

<!DOCTYPE html>
<html>
<head>
<title>Hello</title>
</head>
<body>
<h1 style="text-align: center;">Hello World</h1>
</body>
</html>
'''
listen_socket = socket.socket() # 建立 SOCK 连接
listen_socket.bind(ADDR) # 绑定 IP:端口
listen_socket.listen(100) # 开始监听
print('Server is running: %s:%s ...' % ADDR)
while True:
	client_socket, client_address = listen_socket.accept()# 接收客户端数据
	print('client request from %s:%s' % client_address)
	request = client_socket.recv(1024)
	# 接受客户端的连接
    http_response = RESPONSE
	client_socket.sendall(http_response)
	client_socket.close()
```



####  web框架

数据库连接后端逻辑处理，后段逻辑处理是连接前段界面。

![1568076713641](/home/qx/.config/Typora/typora-user-images/1568076713641.png)





### 常见的web框架

- Django		全能型框架, 大而全, 插件丰富, 文档丰富, 社区活跃, 适合快速开发, 内部耦合比较紧
- Flask            微型框架, 适合新手学习, 极其灵活, 便于二次开发和扩展, 生态环境好, 插件丰富
- Tornado     异步处理, 事件驱动 (epoll), 性能优异
- Bottle          单文件框架, 结构紧凑,适合初学者阅读源码,了解 Web 原理理
- web.py       代码优美, 适合学习源码
- Falcon        性能优异适合写 API 接口口
- Quixote      一个爷爷级别的框架,著名的豆瓣网用的便便是这个
- Sanic           后起之秀,性能秒杀以上所有前辈,但没有前辈们稳定



## Tornado

`pip install tornado`使用包安装，电脑中存在多个环境不建议使用。



```python
#！/bin/env python
import tornado.ioloop
import tornado.web
from tornado.options import parse_command_line, define, options

define("host", default='0.0.0.0', help="主机地址", type=str)
define("port", default=8888, help="主机端口口", type=int)

parse_command_line()
print('你传入入的 host: %s' % options.host)
print('你传入入的 port: %s' % options.port)

class StoryHandler(tornado.web.RequestHandler):
	stories = {1: '小小红帽', 2: '皮皮诺曹', 3: '阿拉丁神灯'}
	def get(self):
		story_id = self.get_argument('story_id')
		story = self.stories[story_id]
		self.write("你想看 %s 的故事" % story)
	def post(self):
		self.get_argument("name")
        self.write('得到了')

class MainHandler(tornado.web.RequestHandler):
	def get(self):
		self.write("Hello, world")
def make_app():
	return tornado.web.Application([
				(r"/", MainHandler),
        		(r"/story", StoryHandler),
		])
if __name__ == "__main__":
	app = make_app()
	app.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```



HTTP请求方式：

- POST            向指定资源提交数据进行处理请求，数据被包含在请求体中。
- GET               请求指定的页面信息，并返回实体主体。
- PUT               从客户端向服务器传送的数据取代指定的文档的内容。
- DELETE        请求服务器删除指定的页面。
- HEAD             类似于get请求，但是获取的内容只有请求头而没有内容。一般用于检测。
- PATCH           对put方法的补充，用于对一直资源进行布局更新。
- OPTIONS     允许客户端查看服务器的性能。





#### 练习

1. 在 MySQL 中建立 user 表, 包含字段: id, name, age, sex, city 等, 并插入若干数据
2. 开发接口,并根据用户传入的 id 显示对应的用户信息
3. 开发接口,并根据用户传入的数值修改用户数据



## 数据库与模板系统

### ORM

ORM 全称是:Object Relational Mapping (对象关系映射)。其主要作用用是在编程中把面向对象的概念
跟数据库中表的概念对应起来。

ORM 的优点:

- 数据模型都在一个地方方定义,更容易更新和维护,也利于重用代码。
- ORM 有现成的工具,很多功能都可以自动完成,比如数据预处理、事务等。
- 它迫使你使用 MVC 架构,ORM 就是天然的 Model,最终使代码更清晰。
- 基于 ORM 的业务代码比较简单,代码量少,语义性好,容易理解。
- 你不必编写性能不佳的 SQL。

#### 惰性

在ORM中的语句不会先执行，只有调用结果的时候才会执行之前sql的语句。



Python下常用的 ORM 有: Django-ORM、SQLAlchemy、Peewee 等

tornado中使用sqlalchemy

代码：

```python
import datetime
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker
from sqlalchemy import Column, String, Integer, Float, Date
from sqlalchemy.ext.declarative import declarative_base

# 建立连接与数据库的连接
engine = create_engine('mysql+pymysql://seamile:54188@localhost:3306/ttt')
Base = declarative_base(bind=engine)
# 创建模型的基础类
Session = sessionmaker(bind=engine)
#创建会话类

class User(Base):
	'''User 模型'''
	__tablename__ = 'user'
	# 该模型对应的表名
	id = Column(Integer, primary_key=True) # 定义 id 字段
	name = Column(String(20), unique=True) # 定义姓名字段
	birthday = Column(Date) # 定义生日字段
	money = Column(Float, default=0.0) # 定义金钱字段
    	
Base.metadata.create_all(checkfirst=True)
# 创建表

session = Session()
# 定义一些对象

bob = User(name='bob', birthday=datetime.date(1990, 3, 21), money=234)
tom = User(name='tom', birthday=datetime.date(1995, 9, 12))
lucy = User(name='lucy', birthday=datetime.date(1998, 5, 14), money=300)
jam = User(name='jam', birthday=datetime.date(1994, 3, 9), money=58)
alex = User(name='alex', birthday=datetime.date(1992, 3, 17), money=99)
eva = User(name='eva', birthday=datetime.date(1987, 7, 28), money=175)
rob = User(name='rob', birthday=datetime.date(1974, 2, 5), money=274)
ella = User(name='ella', birthday=datetime.date(1999, 5, 26), money=394)

# 增加数据
session.add_all([bob, tom, lucy, jam]) # 在 Session 中记录操作
session.commit() # 提交到数据库中执行

# 删除数据
session.delete(jam) # 记录删除操作
session.commit() # 提交到数据库中执行

# 修改数据
tom.money = 270
session.commit() # 提交到数据库中执行

# 查询数据
u_query = session.query(User)
user = u_query.filter_by(id=1).one()
print(user.name)

users = u_query.filter(User.id>2).order_by('birthday')
for u in users:
	print(u.name, u.birthday, u.money)
    
# 直接获取主键(ID)为 5 的数据
user = u_query.get(5)
print(user.id, user.name)

# 使用 filter_by 按条件查询
user = u_query.filter_by(id=7).one()
print(user.id, user.name, user.birthday)

# 使用 filter 进行范围查询,并对结果进行排序
users = u_query.filter(User.id>2).order_by('birthday')
for u in users:
	print(u.name, u.birthday, u.money)

# 根据查询结果进行更新
users.update({'money': User.money - 1}, synchronize_session=False)
sessiom.commit()

# 按数量取出数据: limit / offset
users = u_query.limit(3).offset(4)
for u in users:
	print(u.id, u.name)

# 计数
num = u_query.filter(User.money>200).count()
print(num)

 # 检查是否存在
exists = q.filter_by(name='Seamile').exists()
result = session.query(exists).scalar()
print(result)
```



### Tornado 的模板系统

定义 app 时,在 Application 中定义, 可以是想对路径, 也可以是绝对路径

```
app = Application(
	templates_path = 'templates', # 模版路路径
	static_path = 'statics' # 静态文文件路路径
)
```



#### 模板中的变量

在模板中,变量和表达式使用 {{ ... }} 包围,可以写入任何的 Python **表达式**或者**变量**

html代码：

```html
<!DOCTYPE html>
<html lang='en'>
	<head>
		<meta charset='UTF-8'>
		<title>Templates</title>
	</head>
	<body>
		<div>你好 {{ name }},欢迎回来!</div>
		<div>猜一猜,3 x 2 等于几?</div>
		<div>我就不告诉你等于 {{ 3 * 2 }}</div>
	</body>
</html>
```



#### 从 Python 程序中传递参数

```
class MainHandler(tornado.web.RequestHandler):
	def get(self):
		name = 'Tom'
		say = "Hello, world"
		self.render('index.html', name=name, say=say)
```



#### 模板中的 if...else 结构

模板中的控制语句使用 {% ... %} 包围,如下所示

```html
<p>
	根据您的条件我们进行了筛选
	{% if 条件 %}
		<div>第 1 条数据</div>
		<div>第 2 条数据</div>
		<div>。。。</div>
	{% else %}
		<div>抱歉我们没有找到合适的内容</div>
	{% end %}
</p>
```



#### 模板中的 for 循环

for循环也是用{% for ……%}包围

```
class MainHandler(tornado.web.RequestHandler):
	def get(self):
		students = ["Lucy", "Tom", "Bob"]
		self.render("student.html", students=students)

<html>
	<head>
		<title>学生生信息</title>
	</head>
	<body>
		<ul>
			{% for student in students %}
				<li>{{ student }}</li>
			{% end %}
		</ul>
	</body>
</html>
```



#### 静态文件

⻚面中静态文件的路径需要以 '/static/' 开头, 后面跟文件路径



```
--main.py
--statics
---- img
------ coder.jpg
-- templates
----index.html
```

```html
<img class="avatar" src="/static/img/coder.jpg" />
```



#### 模板的继承



网站中,大多数页面都是同样的结构和风格,我们没有必要在所有页面中把相同的样式重复的写很多遍。

Tornado 为我们提供了模板的继承机制,只需要写好父模板,然后让其他模板继承一下即可

父模板文件名经常定义为 "base.html"

base.html:

```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>{% block title %} 通用用标题 {% end %}</title>
</head>
<body>
		{% block body %}{% end %}
</body>
</html>
```



继承base的子模板：

```
{% extends "base.html" %}

{% block title %} 子页面的标题 {% end %}

{% block body %}
<div>
		子⻚面里的内容
		Bala Bala
</div>
{% end %}
```



## mvc

model ：数据模型层，一般放数据库的表模型

view ：视图，一般存放界面或html

controller：连接model和iew的控制器



模型 (Model), 它是程序需要操作的数据或信息。
视图 (View), 它提供给用户的操作界面, 是程序的外壳。
控制器 (Controller), 它负责根据用户从"视图层"输入的指令, 选取"数据层"中的数据, 然后对其进行相应的操作, 产生最终结果。

```
如sep10_homework：
其中class Student和数据库连接就是model层数据
class MainHandler等页面信息就是iew层数据
而连接model和view，就是controler层的操作
html文件存放在template_path文件夹中
资源文件，如图片、音频放在static文件夹中
```

### 虚拟环境

实现同时存在一个软件的多种版本的虚拟环境。

#### 安装与使用虚拟环境的语句

```
pip install virtualenv
# 安装虚拟环境包

# 在创建虚拟环境之前最好选好虚拟环境安装的文件夹
# 一般虚拟环境与需要使用虚拟环境的项目放在一起
# 虚拟环境可创建在隐藏文件夹中

virtualenv  .enviro
# 创建一个enviro的虚拟环境，新创建的虚拟环境一般只有很少的python包，需要自己重新下载

source ./.enviro/bin/activate 
# 找到虚拟环境中bin文件夹下activate 来激活虚拟环境

deactivate 
# 退出虚拟环境,或者直接关闭终端
```

<strong>虚拟环境实现不用主机执行同一个项目</strong>



```
pip freeze  > requirment.txt
# 创建包名文件

source ./.env/bin/activate # 开启另一个需要装包的环境
pip install -r requirment.txt 
# 下载requrement中的包

```





## 版本控制工具与git

版本控制工具的作用：

- 能够追踪全部代码的状态，blame是一个很重要的东西。
- 能够进行版本之间的差异对比 diff （differece）
- 能够进行版本回滚 checkout <commit_id>
- 能够协助多个开发者进行代码合并 push 、pull

#### 不同版本控制器工具

cvs：很早的版本控制器，基本退出了历史舞台

svn：中心化的版本控制工具，需要一个中心服务器。缺点也在于中心服务器，服务器出现任何问题就完了。

git：分布式版本控制工具，分布广泛，也存在服务器，但是并不必需。

hg：纯python开发的版本控制工具

github：依托于git的平台，有独立的公司在运维，现已被微软收购。

所有文本类的文件都可以交给版本控制工具管理。

### git的历史

linux的创始人之一linus开发的，后交由他人管理。

#### git的使用

```
git config --global user.name 'qiOstrich' 
# 给git一个用户名
git config --global user.email '951850464@qq.com'
# 给git一个邮箱

touch .gitignore 
#  .gitignore 是标注不被git追踪的文件夹及文件的，如 enviro/
这样在使用git就会忽略enviro文件夹

```



| Command  | Description                    | 与远程通信 | 操作示例                                                     |
| -------- | ------------------------------ | :--------: | ------------------------------------------------------------ |
| init     | 在本地初始化一个新的仓库       |     ——     | git init                                                     |
| add      | 添加到暂存区                   |     ——     | git add ./                                                   |
| commit   | 将暂存区的修改提交到本地仓库   |     ——     | git commit -m '注释'                                         |
| push     | 将本地仓库的内容推送到远程仓库 |     有     | git push                                                     |
| pull     | 将远程仓库的更新拉取到本地仓库 |     有     | git pull                                                     |
| clone    | 将远程仓库克隆到本地           |     有     | git clone <br/>https://github.com/qiOstrich/sep11/git        |
| branch   | 创建、管理分支                 |     ——     | git branch bname<br/>git checkout -b bname                   |
| checkout | 切换分支 / 代码回滚 / 代码还原 |     ——     | git checkout bname<br/>git checkout <commit_id><br/>git checkout filename |
| diff     | 不同版本之间进行差异对比       |     ——     | git diff version1 version2                                   |
| merge    | 合并两个分支                   |     ——     | git merge bname                                              |
| status   | 查看当前分支的状态             |     ——     | git status                                                   |
| log      | 查看提交历史                   |     ——     | git log                                                      |
| reset    | 代码重置 / 代码回滚            |     ——     | git reset<br/>git reset filename                             |
| blame    | 检查每行代码最后一次是谁修改的 |     ——     | git blame filename                                           |



git pull 拉取远程仓库文件，

git status 查看状态，找到修改的文件

vim file 

git add file 

git commit -m 'something'

git push



3. 用游戏的方式练习 Git
请点击 [Learn Git Branching](https://learngitbranching.js.org/)
4. 练习
1. 在 Github.com 上建立自己的账号,将前几天写的代码提交并推送上去
2. 每次代码更新后,提交、推送























