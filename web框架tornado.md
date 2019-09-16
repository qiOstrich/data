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





## NOSql、redis、mongodb

如今，大多数的计算机系统（包括服务器、PC、移动设备等）都会产生庞大的数据量。其实，早在2012年的时候，全世界每天产生的数据量就达到了2.5EB。这些数据有很大一部分是由关系型数据库来存储和管理的。实践证明，关系型数据库是实现数据持久化最为重要的方式，它也是大多数应用在选择持久化方案时的首选技术。

NoSQL 是一项全新的数据库革命性运动，虽然它的历史可以追溯到1998年，但是NoSQL真正深入人心并得到广泛的应用是在进入大数据时候以后，业界普遍认为NoSQL是更适合大数据存储的技术方案，这才使得NoSQL的发展达到了前所未有的高度。2012年《纽约时报》的一篇专栏中写到，大数据时代已经降临，在商业、经济及其他领域中，决策将不再基于经验和直觉而是基于数据和分析而作出。事实上，在天文学、气象学、基因组学、生物学、社会学、互联网搜索引擎、金融、医疗、社交网络、电子商务等诸多领域，由于数据过于密集和庞大，在数据的分析和处理上也遇到了前所未有的限制和阻碍，这一切都使得对大数据处理技术的研究被提升到了新的高度，也使得各种NoSQL的技术方案进入到了公众的视野。

NoSQL数据库按照其存储类型可以大致分为以下几类：

| 类型       | 部分代表                            | 特点                                                                                                                                                              |
| ---------- | ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 列族数据库 | HBase<br>Cassandra<br>Hypertable    | 顾名思义是按列存储数据的。最大的特点是方便存储结构化和半结构化数据，方便做数据压缩，对针对某一列或者某几列的查询有非常大的I/O优势，适合于批量数据处理和即时查询。 |
| 文档数据库 | MongoDB<br>CouchDB<br>ElasticSearch | 文档数据库一般用类JSON格式存储数据，存储的内容是文档型的。这样也就有机会对某些字段建立索引，实现关系数据库的某些功能，但不提供对参照完整性和分布事务的支持。      |
| KV数据库   | DynamoDB<br>Redis<br>LevelDB        | 可以通过key快速查询到其value，有基于内存和基于磁盘两种实现方案。                                                                                                  |
| 图数据库   | Neo4J<br>FlockDB<br>JanusGraph      | 使用图结构进行语义查询的数据库，它使用节点、边和属性来表示和存储数据。图数据库从设计上，就可以简单快速的检索难以在关系系统中建模的复杂层次结构。                  |
| 对象数据库 | db4o<br>Versant                     | 通过类似面向对象语言的语法操作数据库，通过对象的方式存取数据。                                                                                                    |

想了解更多的NoSQL数据库，可以访问<http://nosql-database.org/>。

## Redis

Redis 是一种基于键值对的NoSQL数据库，它提供了对多种数据类型（字符串、哈希、列表、集合、有序集合、位图等）的支持，能够满足很多应用场景的需求。Redis将数据放在内存中，因此读写性能是非常惊人的。与此同时，Redis也提供了持久化机制，能够将内存中的数据保存到硬盘上，在发生意外状况时数据也不会丢掉。此外，Redis还支持键过期、地理信息运算、发布订阅、事务、管道、Lua脚本扩展等功能，总而言之，Redis的功能和性能都非常强大，如果项目中要实现高速缓存和消息队列这样的服务，直接交给Redis就可以了。目前，国内外很多著名的企业和商业项目都使用了Redis，包括：Twitter、Github、StackOverflow、新浪微博、百度、优酷土豆、美团、小米、唯品会等。

### 1. Redis简介

2008年，一个名为Salvatore Sanfilippo的程序员为他开发的LLOOGG项目定制了专属的数据库（因为之前他无论怎样优化MySQL，系统性能已经无法再提升了），这项工作的成果就是Redis的初始版本。后来他将Redis的代码放到了全球最大的代码托管平台[Github](<https://github.com/antirez/redis>)，从那以后，Redis引发了大量开发者的好评和关注，继而有数百人参与了Redis的开发和维护，这使得Redis的功能越来越强大和性能越来越好。

Redis是 remote dictionary server 的缩写，它是一个用 ANSI C 编写的高性能的key-value存储系统，与其他的key-value存储系统相比，Redis有以下一些特点（也是优点）：

- Redis的读写性能极高，并且有丰富的特性（发布/订阅、事务、通知等）。
- Redis支持数据的持久化（RDB和AOF两种方式），可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。
- Redis支持多种数据类型，包括：string、hash、list、set，zset、bitmap、hyperloglog等。
- Redis支持主从复制（实现读写分析）以及哨兵模式（监控master是否宕机并自动调整配置）。
- Redis支持分布式集群，可以很容易的通过水平扩展来提升系统的整体性能。
- Redis基于TCP提供的可靠传输服务进行通信，很多编程语言都提供了Redis客户端支持。

### 2. Redis的应用场景

1. 高速缓存  - 将不常变化但又经常被访问的热点数据放到Redis数据库中，可以大大降低关系型数据库的压力，从而提升系统的响应性能。
2. 排行榜 - 很多网站都有排行榜功能，利用Redis中的列表和有序集合可以非常方便的构造各种排行榜系统。
3. 商品秒杀/投票点赞 - Redis提供了对计数操作的支持，网站上常见的秒杀、点赞等功能都可以利用Redis的计数器通过+1或-1的操作来实现，从而避免了使用关系型数据的`update`操作。
4. 分布式锁 - 利用Redis可以跨多台服务器实现分布式锁（类似于线程锁，但是能够被多台机器上的多个线程或进程共享）的功能，用于实现一个阻塞式操作。
5. 消息队列 - 消息队列和高速缓存一样，是一个大型网站不可缺少的基础服务，可以实现业务解耦和非实时业务削峰等特性，这些我们都会在后面的项目中为大家展示。

### 3. Redis的安装和配置

可以使用 Linux 系统的包管理工具 apt 来安装 Redis：
```
apt install redis
#最好把redis服务器也下了
sudo apt install redis-server
```

### 4.Redis 的配置

在redis源代码目录下有一个名为reids.conf的文件 可以使用命令`vim redis.conf` 打开该文件

1.	配置将Redis服务绑定到制定的IP地址和端口

```
bind 127.0.0.1
port 6379
```

2.	设置后台运行
```
daemonize yes
```

3.	设置日志级别，可选： 
```
/*
debug 调试
verbose 详情
notice 通知
warning 警告
*/
loglevel warning
# 设置日志级别为警告
```
4.	配置数据库的数量，默认是16个

```
databases 16
```

5.	配置数据写入规则 （可使用默认值）
```
save 900 1 
# 900 (second) 内修改过1个key，写入一次数据库
save 300 10 
# 300 (s) 内修改过10个key，写入一次数据库
save 60 10000 
# 60(s) 内修改过10000 个key，写入一次数据库
```

6.	配置Redis的持久化机制 -RDB
```
rdbcompression yes   # 压缩 RDB 文件
    rdbchecksum yes      # 对 RDB 文件进行校验
    dbfilename dump.rdb  # RDB 数据库文件的文件名
    dir ./               # RDB 文件保存的目录
```

7.	配置Redis的持久化机制 -AOF 
``` 
appendonly no
appendfilename "appendonly.aof"
```


8. 配置Redis的主从复制，通过主从复制可以实现读写分离。

    ```
    # Master-Replica replication. Use replicaof to make a Redis instance a copy of
    # another Redis server. A few things to understand ASAP about Redis replication.
    #
    #   +------------------+      +---------------+
    #   |      Master      | ---> |    Replica    |
    #   | (receive writes) |      |  (exact copy) |
    #   +------------------+      +---------------+
    #
    # 1) Redis replication is asynchronous, but you can configure a master to
    #    stop accepting writes if it appears to be not connected with at least
    #    a given number of replicas.
    # 2) Redis replicas are able to perform a partial resynchronization with the
    #    master if the replication link is lost for a relatively small amount of
    #    time. You may want to configure the replication backlog size (see the next
    #    sections of this file) with a sensible value depending on your needs.
    # 3) Replication is automatic and does not need user intervention. After a
    #    network partition replicas automatically try to reconnect to masters
    #    and resynchronize with them.
    #
    replicaof 主机IP地址 主机端口
    ```

9. 配置慢查询。

    ```
    slowlog-log-slower-than 10000  # 一次操作超过 10000 毫秒被视作一次慢查询
    slowlog-max-len 128            # 最多纪录 128 次满查询
    ```

### 5. Redis的服务器和客户端

接下来启动 Redis 服务器，下面的方式将以指定的配置文件启动 Redis 服务。

```Shell
redis-server redis.conf
```

接下来用 Redis 客户端去连接服务器。

```Shell
redis-cli -h localhost -p 6379
```

Redis有着非常丰富的数据类型，也有很多的命令来操作这些数据，具体的内容可以查看[Redis命令参考](http://redisdoc.com/)，在这个网站上，除了Redis的命令参考，还有Redis的详细文档，其中包括了通知、事务、主从复制、持久化、哨兵、集群等内容。

![redis-data](./img/redis-data-types.png)

```Shell
127.0.0.1:6379> set username admin
OK
127.0.0.1:6379> get username
"admin"
127.0.0.1:6379> set password "123456" ex 300
OK
127.0.0.1:6379> get password
"123456"
127.0.0.1:6379> ttl username
(integer) -1
127.0.0.1:6379> ttl password
(integer) 286
127.0.0.1:6379> hset stu1 name hao
(integer) 0
127.0.0.1:6379> hset stu1 age 38
(integer) 1
127.0.0.1:6379> hset stu1 gender male
(integer) 1
127.0.0.1:6379> hgetall stu1
1) "name"
2) "hao"
3) "age"
4) "38"
5) "gender"
6) "male"
127.0.0.1:6379> hvals stu1
1) "hao"
2) "38"
3) "male"
127.0.0.1:6379> hmset stu2 name wang age 18 gender female tel 13566778899
OK
127.0.0.1:6379> hgetall stu2
1) "name"
2) "wang"
3) "age"
4) "18"
5) "gender"
6) "female"
7) "tel"
8) "13566778899"
127.0.0.1:6379> lpush nums 1 2 3 4 5
(integer) 5
127.0.0.1:6379> lrange nums 0 -1
1) "5"
2) "4"
3) "3"
4) "2"
5) "1"
127.0.0.1:6379> lpop nums
"5"
127.0.0.1:6379> lpop nums
"4"
127.0.0.1:6379> rpop nums
"1"
127.0.0.1:6379> rpop nums
"2"
127.0.0.1:6379> sadd fruits apple banana orange apple grape grape
(integer) 4
127.0.0.1:6379> scard fruits
(integer) 4
127.0.0.1:6379> smembers fruits
1) "grape"
2) "orange"
3) "banana"
4) "apple"
127.0.0.1:6379> sismember fruits apple
(integer) 1
127.0.0.1:6379> sismember fruits durian
(integer) 0
127.0.0.1:6379> sadd nums1 1 2 3 4 5
(integer) 5
127.0.0.1:6379> sadd nums2 2 4 6 8
(integer) 4
127.0.0.1:6379> sinter nums1 nums2
1) "2"
2) "4"
127.0.0.1:6379> sunion nums1 nums2
1) "1"
2) "2"
3) "3"
4) "4"
5) "5"
6) "6"
7) "8"
127.0.0.1:6379> sdiff nums1 nums2
1) "1"
2) "3"
3) "5"
127.0.0.1:6379> zadd topsinger 5234 zhangxy 1978 chenyx 2235 zhoujl 3520 xuezq
(integer) 4
127.0.0.1:6379> zrange topsinger 0 -1 withscores
1) "chenyx"
2) "1978"
3) "zhoujl"
4) "2235"
5) "xuezq"
6) "3520"
7) "zhangxy"
8) "5234"
127.0.0.1:6379> zrevrange topsinger 0 -1
1) "zhangxy"
2) "xuezq"
3) "zhoujl"
4) "chenyx"
127.0.0.1:6379> geoadd pois 116.39738549206541 39.90862689286386 tiananmen 116.27172936413572 39.99
135172904494 yiheyuan 117.27766503308104 40.65332064313784 gubeishuizhen
(integer) 3
127.0.0.1:6379> geodist pois tiananmen gubeishuizhen km
"111.5333"
127.0.0.1:6379> geodist pois tiananmen yiheyuan km
"14.1230"
127.0.0.1:6379> georadius pois 116.86499108288572 40.40149669363615 50 km withdist
1) 1) "gubeishuizhen"
   2) "44.7408"
```



































