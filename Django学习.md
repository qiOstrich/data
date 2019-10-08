# Django学习

## C/S & B/S

```
S:B browser 浏览器   S server  服务器   主流
CS:C client  客户端   S server  服务器
B/S结构是WEB兴起后的一种网络结构模式，WEB浏览器是客户端最主要的应用软件。这种模式统一了客户端，将系统功能实现的核心部分集中到服务器上，简化了系统的开发、维护和使用。
```

### cs，bs的区别

硬件环境：

- bs只需要有浏览器就可以实现，对操作系统无特殊要求，可以跨系统，需要广域网。
- cs需要有相同的操作系统，可以再局域网内使用。

客户端：

- bs对电脑配置要求较低。
- cs需要有相对较高的电脑配置。

软件安装：

- bs只需要一个浏览器。
- cs需要在使用前安装客户端软件。

升级和维护：

- bs不需要安装和维护。
- cs的每一个客户端都需要安装和维护。

安全性：

- bs不怎么安全，传送报文容易被获取。
- cs有权限多层校验，传送的信息不易被获取，安全性较高。



### cs/bs的应用语言

```
CS/BS
	客户端和服务器的交互模型
		Client
			客户端
		Browser
			浏览器
		Server
		
			Web后端
				python
					django     8
					flask      1
					tornado    1
				java
					struts2/struts1
					hibernate
					spring
					springmvc
					mybatis
					springboot
					springclude
				php
					yii
					ci
					thinkphp
```



## MVC

程序编写架构思想：用于解耦合，提高内聚。

```
MVC：软件架构思想
	简介：
		MVC开始是存在于桌面程序中的，M是指业务模型 model，V是指用户界面 view，C则是控制器 controler，使用MVC的目的是将M和V的实现代码分离，从而使同一个程序可以使用不同的表现形式。比如一批统计数据可以分别用柱状图、饼图来表示。C存在的目的则是确保M和V的同步，一旦M改变，V应该同步更新
实现了模型层的复用
	核心思想: 
		解耦合
	面向对象语言：高内聚  低耦合
	Model
		模型
		封装数据的交互操作
			CRUD
	View
		视图
		是用来将数据呈现给用户的
	Controller
		控制器
		接受用户输入输出
		用来协调Model和View的关系，并对数据进行操作，筛选
	流程
		控制器接受用户请求
		调用模型，获取数据
		控制器将数据展示到视图中
```

## MTV

mvc的python使用模式，与mvc思想相同，名字不同。

```
MTV
	也叫做MVT
	本质上就是MVC，变种
	Model
		同MVC中Model
	Template
		模板
		只是一个html，充当的是MVC中View的角色，用来做数据展示
	Views
		视图函数
		相当于MVC中Controller
```



## Django介绍

```
Django是一个开放源代码的Web应用框架，它最初是被开发来用于管理劳伦斯出版集团旗下的一些以新闻内容为主的网站的，即是CMS（内容管理系统）软件。并于2005年7月在BSD许可证下发布。这套框架是以比利时的吉普赛爵士吉他手Django Reinhardt来命名的。
	重量级，替开发者想了太多的事情，帮开发者做了很多的选择，内置了很多的功能
官方网站
	http://www.djangoproject.com
使用版本1.11.7
	LTS：长期支持版本
	以后再学2.2 LTS
```

### 虚拟环境

```
一般在开发前都会配置虚拟环境，用于分割同时开发的多个项目。

virtualenv 目录/environment_name # 新建一个环境

source 目录/environment_name/bin/activate  # 应用虚拟环境

pip freeze # 查看当前环境的第三方包
pip list # 也是查看当前环境的包，显示与freeze不同

#导出环境配置
pip freeze > 目录/requirments.txt # 新建或覆盖配置信息文件

pip install -r 目录/requirments.txt # 根据文件内容下载包

deactivate 退出当前虚拟环境

```

### 虚拟化技术

```
虚拟化技术
	（1）虚拟机      
	（2）虚拟容器
		Docker  
			支持很多种语言
	（3）虚拟环境--迷你
		python专用
		将python依赖隔离
```

### 安装Django

```
pip install django
		pip install django==1.11.7   一定要使用==
		pip install django==1.11.7 -i https://pypi.douban.com/simple  豆瓣源
	查看django是否安装成功
		pip freeze
		pip list
		进入python环境
			import django
			django.get_version()
```

### 创建django项目

```
终端创建：
	django-admin startproject  目录/Django_project_name

pycharm专业版（社区版建议使用终端创建，在打开项目）
直接创建Django项目，只需要修改项目目录即可，环境可以新建，可以选择已有的虚拟环境

一个django项目下有的文件夹和文件：
项目同名文件夹，主目录
- __init__.py
- settings.py
- urls.py
- wsgi.py
- views （手动创建，一般不会再主目录创建试图，虽然可以用）



添加app-子目录
命令：django-admin startapp 目录/app_name
子目录：
- migrations文件夹 自带__init__.py文件
- __init__.py
- admin.py　        ＃后台管理
- apps.py　　　  ＃应用配置
- models.py          ＃模型
- tests.py　　　  ＃　单元测试
- views.py　　　＃视图函数　
```



###  项目结构

```
项目结构
	项目名字
		manage.py
			管理整个项目的文件
			以后的命令基本都通过他来调用
		项目名字
			__init__
				python包而不是一个文件夹
			settings
				项目全局配置文件
					ALLOWED_HOST=["*"]
					修改settings
						LANGUAGE_CODE='zh-hans'
						TIME_ZONE='Asia/Shanghai'
			urls
				根路由
					url（p1,p2）
			wsgi
				用在以后项目部署上，前期用不到
				服务器网关接口
				webserver gateway interface
```

###　手动修改配置

```
settings.py:
ALLOWED_HOSTS = ['*']

INSTALLED_APPS=[在原有的字符串列中+，'App','BaseApp','TwoApp','ThreeApp']

TEMPLATES=[{'DIRS':[os.path.join(BASE_DIR,'templates')]}]

DATABASES={
	'default':{
		'ENGINE':'django.db.backends.mysql',
		'NAME':'database_name',
		'USER':'qmx',
		'PASSWORD':'123',
		'HOST':'localhost',
		'PORT':'3306',
	}
}

LANGUAGE_CODE = 'zh-hans'

TIME_ZONE = 'Asia/Shanghai'

USE_TZ = False
```



```
启动项目
	python manage.py runserver
		使用开发者服务器启动项目
		默认会运行在本机的 8000端口上
	启动服务器命令
    (1)python manage.py runserver
    (2)python manage.py runserver 9000
    (3)python manage.py runserver 0.0.0.0:9000
    # 不能单独出现主机号
```

### 路由拆分

```
在子目录中创建路由文件：
urls.py
urlpattrens=[
	url(r"^index",views.viewMethod),
	
]

在根路由中增加：
url('^appname/',inclue('appName.urls')),

在页面中访问需要加appname/路由名：
http://localhost:8000/app/index/
```



### 写第一个请求

```
1.编写一个路由
      url(p1, p2)
              url(r'^index/',views.index),
      p1 正则匹配规则
      p2 对应的视图函数
2.编写视图函数
	（1）本质上还是一个函数
		def index(request):
    		return HttpResponse('123')
		要求：只是默认第一个参数是一个request，必须返回一个response
	（2）返回值：
		1.HttpResponse()
			HttpResponse('123')
			HttpResponse('<h1>123</h1>')  # html标签会被解析
	    2.render
			在App下创建templates
				注意名字是固定的，不能打错单词
			render方法的返回值类型也是一个HttpResponse类型的
			要求：
				第一个参数是request，第二个参数的是页面
	********注意需要在settings里的INSTALLED_APPS设置App路径*****
	将应用注册到项目的settings中INSTALLED_APPS中
             加载路由的方式
                  INSTALLED_APPS---》‘Two’
                  INSTALLED_APPS---》‘Two.apps.TwoConfig’  版本限制 1.9之后才能使用
3.模板配置有两种情况
		①在App中进行模板配置
		  - 只需在App的根目录创建templates文件夹即可
		  - 必须在INSTALLED_APP下安装app
		②在项目目录中进行模板配置
		  - 需要在项目目录中创建templates文件夹并标记
		  - 需要在settings中进行注册  settings--》TEMPLATES--》DIRS-					    												os.path.join(BASE_DIR,'templates')
		  注意：开发中常用项目目录下的模板    理由：模板可以继承，复用
```



### Django的工作机制！！！必备知识

```
1.用manage .py runserver 启动Django服务器时就载入了在同一目录下的settings .py。该文件包含了项目中的配置信息，如URLConf等，其中最重要的配置就是ROOT_URLCONF，它告诉Django哪个Python模块应该用作本站的URLConf，默认的是urls .py

2.当访问url的时候，Django会根据ROOT_URLCONF的设置来装载URLConf。

3.然后按顺序逐个匹配URLConf里的URLpatterns。如果找到则会调用相关联的视图函数，并把HttpRequest对象作为第一个参数(通常是request)

4.最后该view函数负责返回一个HttpResponse对象。
```

### 模板显示

```
与flask模板差不多

显示在模板中
	先挖坑
		{{ var }}
	再填坑
		渲染模板的时候传递上下文进来
		上下文是一个字典
		content={'key':'value'}
	模板的兼容性很强
		不传入不会报错
		多传入也会自动优化掉
	浏览器不认模板
		浏览器也叫做html解析器  只识别html文件
		在到达浏览器之前，已经进行了转换，将模板语言转换成了HTML
	for 支持
		{% for %}
	render底层实现：应用场景，发送邮件，邮件的内容需要使用render方法来操纵
		加载
			three_index = loader.get_template('three.html')
			content={'xxx':'xxxx'}
		渲染
			result = three_index.render(content=content)
			return HttpResponse(result)
```

### 修改到mysql数据库

```
在settings中的DATABASES中进行修改
实际上都是关系型数据库
mysql
	'ENGINE': 'django.db.backends.mysql',
	NAME
		数据库名字
	USER
		用户名字
	PASSWORD
		密码
	HOST
		主机
	PORT
		端口号
			引号加不加“”都可以			
实际例子：
DATABASES={
	'default':{
		'ENGINE':'django.db.backends.mysql',
		'NAME':'database_name',
		'USER':'qmx',
		'PASSWORD':'123',
		'HOST':'localhost',
		'PORT':'3306',
	}
}

mysql迁移---》有坑---驱动问题
mysql驱动
	mysqlclient
		- python2,3都能直接使用
		- 致命缺点
		- 对mysql安装有要求，必须指定位置存在配置文件
	mysql-python
		- python2 支持很好
		- python3 不支持
	pymysql
		会伪装成mysqlclient和mysql-python
		- python2，python3都支持
		init.py中   import  pymysql      pymysql.install_as_mysqldb()
```

### DML(模型迁移，表操作)

```
数据操作
	迁移
		生成迁移
			python manage.py makemigrations
		执行迁移
			python manage.py migrate
			才会真正在数据库产生表
	ORM
		Object Relational Mapping 对象关系映射
		将业务逻辑和sql进行了一个解耦合
		通过models定义实现  数据库表的定义
	模型定义
		（1）继承models.Model
		（2）会自动添加主键列
		（3）必须指定字符串类型属性的长度
			class Student(models.Model):
                 name = modes.CharField(max_length=16)
                 age = models.IntegerField(default=1)
	存储数据
		创建对象进行save()
	数据查询
		模型.objects.all()
		模型.objects.get(pk=2)
	更新
		基于查询
		save()
	删除
		基于查询
		delete()
```



### django shell

```
在终端中可以执行某一块的代码：
	通常用来调试

python manage.py shell
	django 终端
		python manager.py shell
	集成了django环境的python 终端
	eg：
	from Two.models import Student
	students = Student.objects.all()
    for student in students:
             print(students.name)
```

### 数据级联：一对多

```
模型关系：
     class Grade(models.Model):
      		g_name = models.CharField(max_length=32)
    class Student(models.Model):
          s_name =models.CharField(max_length=16)
          s_grade=models.ForeignKey(Grade) 
 多获取一 # 显性属性
	就是一个书写的属性
	eg:根据学生找班级名字
        student = Student.objects.get(pk=2)
        grade = student.s_grade
        return HttpResponse(grade.g_name)
一获取多 # 隐形属性
	多的set
	eg:根据班级  找所有的学生
        grade = Grade.objects.get(pk=2)
        students = grade.student_set.all()
        content = {
                    'students':students
        }
        return render(request,'students_list.html',content)    
```



###　元信息

```
在模型文件中，models.py的类中加元信息，可以改变创建表名
class Dog(models.Model):
	可以定义id，也可以不指定主键，django会自动创建主键，
	name = models.CharField(max_length=32) # 一定要制定最大长度
	age = models.IntegerField() # default 可以设置默认值
	
	class Meta:
	managed = False # 是migrate迁移忽略这个类
	db_table = 'dogs'

class Meta：指定表名和字段名字
     db_table = '表名'
     注意：表的字段一般都是下划线  eg：s_name
           类的属性一般都是驼峰式  eg: sName
```

### 定义字段

```
字段类型：
	CharField,
	TextField,
	IntegerField,
	FloatField,
	BooleanField,
	DecimalField, # 特定浮点数，精度更高，一般应用于金融
	NullBooleanField # 有三个值：null，true，false，存在的意义是存储空间小
	AutoField，
	FileField，
	ImageField， 图片，继承自fileField，
	DateField,
	DateTimeField,
	TimeField,
	
字段约束：
	max_length, #长度限制
	default, #默认值
	unique, # 值唯一
	db_index, # 索引
	null, # 是否可空
	primary_key, # 主键
	db_column， # 表中的字段名
```



### 模型过滤

```
filter 返回符合条件的筛选结果。
exclude 返回不符合条件的筛选结果。

Django默认通过模型的objects对象实现模型数据查询。
Django有两种过滤器用于筛选记录：
	filter:返回符合筛选条件的数据集
	exclude	:返回不符合筛选条件的数据集
链式调用：
	多个filter和exclude可以连接在一起查询
	Person.objects.filter().filter().xxxx.exclude().exclude().yyyy
	Person.objects.filter(p_age__gt=50).filter(p_age__lt=80)注意数据类型
	Person.objects.exclude(p_age__gt=50)
	Person.objects.filter(p_age__in=[50,60,61])
```

### 创建对象的方式

```
创建对象的方式
	（1）创建对象1   常用
		person = Person（）   person.p_name='zs'  person.p_age=18
	（2）创建对象2
		直接实例化对象，设置属性
		创建对象，传入属性
		使用person =  Model.objects.create(p_name='zs',p_age=18)
			person.save()
		自己封装类方法创建
		在Manager中封装方法创建
	（3）创建对象3
		person = Person(p_age=18)
	（4）创建对象4
		注意:__init__已经在父类models.Model中使用，在自定义的模型中无法使用
		在模型类中增加类方法去创建对象
		@classmethod  
        def create(cls,p_name,p_age=100):
                  return cls(p_name=p_name,p_age=p_age)
        person = Person.create('zs')
```

### 查询集queryset

```
过滤器：过滤器就是一个函数，基于所给的参数限制查询集结果，返回查询集的方法称为过滤器。
       查询经过过滤器筛选后返回新的查询集，所以可以写成链式调用。
       获取查询结果集  QuerySet
	all
		模型.objects.all()
	filter
		模型.objects.filter()
	exclude
		模型.objects.exclude()
	order_by
		persons= Person.objects.order_by('id')
			默认是根据id排序
			注意要写的是模型的属性
	values
		persons= Person.objects.order_by('id') 
		persons.values()
		注意方法的返回值类型   是字典
	切片
		限制查询集，可以使用下标的方法进行限制
			左闭右开区间
		不支持负数
			下标没有负数
		实际上相当于 limit  offset
		studentList = Student.objects.all()[0:5]  
			第一个参数是offset  第二个参数是limit
	懒查询/缓存集
		查询集的缓存：每个查询集都包含一个缓存，来最小化对数据库的访问
		在新建的查询集中，缓存首次为空，第一次对查询集求值，会发生数据缓存，django会将查询出来的数据做	一个缓存，并返回查询结果，以后的查询直接使用查询集的缓存。
		- 都不会真正的去查询数据库
		
		- 懒查询
        - 只有我们在迭代结果集，或者获取单个对象属性的时候，它才会去查询数据
        - 为了优化我们结果和查询
```

```
例子：
# all 得到表中的所有数据
def testQuery(request):
    animals = Animals.objects.all()
    for an in animals:
        print(an.id, an.name, an.hoster_id)
    return HttpResponse('That is that.')
    
# exclude 得到不符合条件的对象（筛选条件之外）
def testQueryExclude(request):
    animals = Animals.objects.exclude(hoster_id__lt=3)
    for an in animals:
        print(an.id, an.name, an.hoster_id)
    return HttpResponse('That is that.')
    
# order_by 得到的结果按照某字段排序，参数需要是字符串
def testOrderBy(request):
    animals = Animals.objects.order_by('hoster_id')
    for an in animals:
        print(an.id, an.name, an.hoster_id)
    return HttpResponse('That is that.')
    
# values 转换得到的结果
def testValues(request):
    animals = Animals.objects.all()
    animals = animals.values()
    for an in animals:
        print(an.get('id'), an.get('name'), an.get('hoster_id'))
    return HttpResponse('That is that.')

# 切片 可以完成分页原代码实现
def testCut(request):
    page = 1
    per_page = 5
    animals = Animals.objects.order_by('hoster_id')[((page - 1) * per_page):(per_page * page)]
    for an in animals:
        print(an.id, an.name, an.hoster_id)
    return HttpResponse('That is that.')
```



```
获取单个对象：
得到的结果就是一个对象
	get
		不存在会抛异常  DoesNotExist
		存在多于一个 MultipleObjectsReturned
		使用这个函数 记得捕获异常
	last
		返回查询集种的最后一个对象
	first
		需要主动进行排序
		persons=Person.objects.all().first()
	内置函数：框架自己封装得方法 帮助我们来处理业务逻辑
		count
			返回当前查询集中的对象个数
				eg：登陆
		exists
			判断查询集中是否有数据，如果有数据返回True没有反之
```

```
例子：
# first 得到数据库中第一个数据
def testFirst(request):
    dog = Animals.objects.first()
    print(dog.id, dog.name, dog.hoster_id)
    return HttpResponse('You getted it.')

# last 得到数据库中最后一个数据
def testLast(request):
    animal = Animals.objects.last()
    print(animal.id, animal.name, animal.hoster_id)
    return HttpResponse('You getted it.')
    
# get 按照主键查找一个数据
def testGet(request):
    animal = Animals.objects.get(pk=5)
    print(animal.id, animal.name, animal.hoster_id)
    return HttpResponse('You getted it.')

# count 和exists 多用来判断结果存在与非
count：
def testCount(request):
    animal = Animals.objects.filter(hoster_id__gt=20)
    if animal.count() > 0:
        print(animal.id, animal.name, animal.hoster_id)
    else:
        print('么得东西呀')
    return HttpResponse('You getted it.')
    
exists：
def testExists(request):
    animal = Animals.objects.filter(hoster_id__gt=20)
    if animal.exists():
        print(animal.id, animal.name, animal.hoster_id)
    else:
        print('么得东西呀')
    return HttpResponse('You getted it.')
```



```
字段查询：
	对sql中where的实现，作为方法filter(),exclude(),get()的参数
	语法:属性名称__比较运算符=值
		Person.objects.filter(p_age__gt=18)
	条件
		属性__操作符=临界值
		gt
			great than
		gte
			great than equals
		lt
			less than
		lte
			less than equals
		gt,gte,lt,lte：大于，大于等于，小于小于等于filter(sage__gt=30)
		in
			in：是否包含在范围内,filter(pk__in=[2,4,6,8])
				单引号可以使用
		exact**********************************************************************************
			exact：判断，大小写不敏感，filter(isDelete = False)
		startswtith
			类似于 模糊查询 like
		endswith
			以 xx 结束  也是like
		contains
			contains：是否包含，大小写敏感，filter(sname__contains='赵')
		isnull,isnotnull
			isnull,isnotnull：是否为空，filter(sname__isnull=False)
		ignore 忽略大小写
			iexact*******************************************************************************
			icontains
			istartswith
			iendswith
			以上四个在运算符前加上 i(ignore)就不区分大小写了 iexact...
```

```
例子：
def testSpecifical(request):
    animals1 = Animals.objects.filter(hoster_id__gt=5)
    animals2 = Animals.objects.filter(hoster_id__gte=5)
    animals3 = Animals.objects.filter(hoster_id__lt=5)
    animals4 = Animals.objects.filter(hoster_id__lte=5)
    animals5 = Animals.objects.filter(hoster_id__in=[1, 2, 3])
    animals6 = Animals.objects.filter(hoster_id__exact=3)
    animals7 = Animals.objects.filter(name__exact= '柴犬')
    animals8 = Animals.objects.filter(name__startswith='暹')
    animals9 = Animals.objects.filter(name__endswith='狗')
    animals10 = Animals.objects.filter(name__contains='狗')
    animals11 = Animals.objects.filter(name__isnull=False)
    if animals11.count() ==0:
        return HttpResponse('么得东西呀')
    for i in animals11:
        print(i.id, i.name,i.hoster_id)
    return HttpResponse('OK')
其中exact，startswith，endswith，contains前面都可以加i 表示ignore（忽略大小写）
```



```
查询时间：
models.DateTimeField(auto_now_add=True)
	year
	month 会出现时区问题  需要在settings中的USE-TZ中设置为 False
	day
	week_day
	hour
	minute
	second
	orders = Order.objects.filter(o_time__month=9)
		有坑：时区问题
			关闭django中自定义的时区
				USE-TZ=False
			在数据库中创建对应的时区表
```

```
例子：
def testDatatime(request):
    result =Fobject.objects.filter(datatime__day=22)
    for res in result:
        print(res.id,res.num_a,res.num_b,res.datatime)
    return HttpResponse('也海星')
    
def testDatatime(request):
    result =Fobject.objects.filter(datatime__year__gt=2000)
    for res in result:
        print(res.id,res.num_a,res.num_b,res.datatime)
    return HttpResponse('也海星')
    
# 比较月份前设置settings中的USE_TZ=False （use timezone）
def testDatatime(request):
    result =Fobject.objects.filter(datatime__month__gt=6)
    for res in result:
        print(res.id,res.num_a,res.num_b,res.datatime)
    return HttpResponse('也海星')

```



```
注意：mysql oracle中所说的聚合函数 多行函数  组函数 都是一个东西  max min avg sum count
聚合函数/组函数/多行函数/高级函数
	模型：
      class Customer(models.Model):
          c_name = models.CharField(max_length=16)
          c_cost = models.IntegerField(default=10)
	使用：
      使用aggregate()函数返回聚合函数的值
      Avg：平均值
      Count：数量
      Max：最大
      Min：最小
      Sum：求和
      eg:Student.objects.aggregate(Max('age'))
```

```
例子：
def testAggregate(request):
    avg = Fobject.objects.aggregate(Avg('num_a'))
    count = Fobject.objects.aggregate(Count('num_a'))
    max = Fobject.objects.aggregate(Max('num_a'))
    min = Fobject.objects.aggregate(Min('num_a'))
    sum = Fobject.objects.aggregate(Sum('num_a'))
    print(avg, count, max, min, sum)
    return HttpResponse('好样的')


```



```
跨关系查询。
外键的使用：
	模型：
		class Grade(models.Model):
    		g_name = models.CharField(max_length=16)
        class Student(models.Model):
            s_name = models.CharField(max_length=16)
            s_grade = models.ForeignKey(Grade)
    使用：
        模型类名__属性名__比较运算符，实际上就是处理的数据库中的join
        Grade  ---g_name      Student---》s_name  s_grade（外键)
        gf = Student.objects.filter(name='凤姐')
        print(gf[0].s_grade.name)
        grades = Grade.objects.filter(student__s_name='Jack')
        查询jack所在的班级
```

```
例子：
class Master(models.Model):  # 主人
    class Meta:
        db_table = 'master'
    name = models.CharField(max_length=32)
    age = models.IntegerField(default=18)
    
class Animals(models.Model):# 宠物/动物
    class Meta:
        db_table = 'animals'
    name = models.CharField(max_length=32)
    hoster = models.ForeignKey(Master)

def getPets(request): # 通过主键对象找外键对象
    master = Master.objects.filter(id=1)[0]
    animals = master.animals_set.all()
    for i in animals:
        print(i.id, i.name)
    return HttpResponse("Yes")
    
def findHoster(request): # 通过外键对象找主键对象
    dog = Animals.objects.first()
    host = dog.hoster
    print(dog.name)
    print(host.id)
    return HttpResponse('You getted it.')
```

#### F对象（字段间比较）

```
F对象.表内字段的值的比较
	模型：
		class Company(models.Model):
              c_name = models.CharField(max_length=16)
              c_gril_num = models.IntegerField(default=5)
              c_boy_num = models.IntegerField(default=3)
	F：
		获取字段信息，通常用在模型的自我属性比较，支持算术运算
	eg:男生比女生少的公司
	companies = Company.objects.filter(c_boy_num__lt=F('c_gril_num'))
	eg:女生比男生多15个人
	companies = Company.objects.filter(c_boy_num__lt=F('c_gril_num')-15)
```

```
例子：
def testF(request):
    result = Fobject.objects.filter(num_a__gt=F('num_b'))
    for res in result:
        print(res.id, res.num_a, res.num_b, res.datatime)
    return HttpResponse('好样的')
```

#### G对象（逻辑运算）

```
Q对象 eg：常适用于逻辑运算 与或非（一般都可以通过练市调用代替）
		年龄小于25：
            Student.objects.filter(Q(sage__lt=25))
        eg:男生人数多余5 女生人数多于10个：
             companies = Company.objects.filter(c_boy_num__gt=1).filter(c_gril_num__gt=5)
             companies = Company.objects.filter(Q(c_boy_num__gt=5)|Q(c_gril_num__gt=10))
        支持逻辑运算：
                    与或非
                    &
                    |
                    ~
        年龄大于等于的：
					Student.objects.filter(~Q(sage__lt=25))
```

```
例子：
def testG(request):
    result11 = Fobject.objects.filter(Q(num_a__gt=F('num_b'))&Q(datatime__day__gt=1))
    result12 = Fobject.objects.filter(Q(num_a__gt=F('num_b'))|Q(datatime__day__gt=1))
	result13 = Fobject.objects.filter(~(Q(num_a__gt=F('num_b'))|Q(datatime__day__gt=1)))

    for res in result12:
        print(res.id, res.num_a, res.num_b, res.datatime)
    return HttpResponse('好样的')
```





## Template

一般模板文件夹创建在根目录下。

使用模板需要在settings中添加路径

```
概念：模板
	在Django框架中，模板是可以帮助开发者快速生成，呈现给用户页面的工具
	模板的设计方式实现了我们MVT中VT的解耦，VT有着N:M的关系，一个V可以调用任意T，一个T可以供任意V使用
	模板处理分为两个过程
		加载
		渲染
	模板中的动态代码段除了做基本的静态填充，可以实现一些基本的运算，转换和逻辑
	早期的web服务器  只能处理静态资源请求  模板能处理动态资源请求 依据计算能生成相应的页面
	注意：在Django中使用的就是Django模板，在flask种使用得是jinja2模板
```

```
模板组成：模板主要有2个部分
			① HTML静态代码
			② 动态插入的代码段（挖坑，填坑）
```

### 模板语法

#### 变量

```
与flask相同使用：
{{ variable }}

在views视图函数中使用context传，最好定义一个字典。
```

```
例子：
views.py:
context = {
        'name': '老王',
    }
    return render(request,'base.html',context=context)
base.html:
{{ name }}
```

#### 模板中的点语法

````
模版中的点语法
	属性或者方法
		student.name/student.getname
		class Student(models.Model):
    		s_name = models.CharField(max_length=16)
			def get_name(self):
        		return self.s_name
	弊端：模板中的小弊端，调用对象的方法，不能传递参数 为什么不能传递参数  因为连括号都没有
	索引	students.0.gname
	字典  student_dict.hobby
````

```
与flask差不多，
差别在可以传无参函数。调用不使用括号。
```

#### 标签：

##### for

```
功能标签：（for）
              for
                  for i in xxx
                  empty
                      {% empty %}
                      判断之前的代码有没有数据 如果没有显示empty下面的代码
                      eg:{% for 变量 in 列表 %}
                              语句1 
                                 {% empty %}
                              语句2
                          {% endfor %}
                  forloop
                      循环状态的记录
                      {{ forloop.counter }} 表示当前是第几次循环，从1数数
                      {{ forloop.counter0}}表示当前是第几次循环，从0数数
                      {{ forloop.revcounter}}表示当前是第几次循环，倒着数数，到1停
                      {{ forloop.revcounter0}}表示当前第几次循环，倒着数，到0停
                      {{ forloop.first }} 是否是第一个  布尔值
                      {{ forloop.last }} 是否是最后一个 布尔值
```

##### if

```
功能标签：（if）
                  if
                      分支
                      判断
                      if - else
                      if - elif -else
```

##### 注释

```
注释：
          单行注释
              {#  被注释掉的内容  #}
          多行注释
              {% comment %}
              内容
          	  {% endcomment %}
          	  或者选中行，使用control+ /
```

##### withratio

```
withratio
            乘
            {% widthratio 数  分母  分子  %}
            {% widthratio count 1 5 %}
```

##### 整除divisibleby

```
整除：{% if num|divisibleby:2 %}
                      整除
                      {% if forloop.counter|divisibleby:2%}
                      奇偶行变色
```

##### 判断是否相等

```
ifequal： 
        ifequal
            {%  ifequal  value1 value2 %}
                语句
        {% endifequal %}
            {% ifequal forloop.counter 5 %}
```

#### 过滤器

```
	|
	将前面的输入作为后面的输出
	add：
		<h4>{{ count|add:2 }}</h4>
		<h4>{{ count|add:-2 }}</h4>
	upper：
	lower：
	safe
		确认安装
		进行渲染
		eg:
              code = """
                  <h2>睡着了</h2>
                  <script type="text/javascript">
                      var lis = document.getElementsByTagName("li");

                      for (var i=0; i< lis.length; i++){
                          var li = lis[i];
                          li.innerHTML="日本是中国领土的一部分!";
                      }
                  </script>
                   """
	endautoescape：
		{% autoescape off%}
			code
		{% endautoescape %}

```

#### 结构标签 block，include，extends,block.super

```
结构标签
	block
		块
		坑
		用来规划页面布局，填充页面
			首次出现代表规划
			第二次c出现代表填坑
			第三次出现也代表填坑，默认会覆盖
			第N次...
			如果不想被覆盖  block.super
	extends
		继承
		面向对象的体现
		提高模板的复用率
	include
		包含
		将其它模板作为一部分，包裹到我们的页面中
```

#### 加载静态资源

```
加载静态资源
	static--》 html  css js  img font
	静态资源路径 /static/css/xxx.css
		不推荐
		硬编码
	需要在settings中添加  STATICFILES_DIRS=[os.path.join(BASE_DIR,'static')]
	推荐
		{% load static%}
		{%static,'css/xxx.css'%}
		思考：html和模板中的页面  都可以使用load吗？  注意必须在模板中使用
	坑点：仅在DEBUG模式下可以使用  如果settings中的DEBUG=False 那么是不可以使用的
```

```
setting中手动添加语句
STATICFILES_DIRS=[os.path.join(BASE_DIR,'static')]

尽量使用
{% load static %}
{% static 'js/name.js' %}
```

### 常见的请求状态码

```
请求状态码
	2xx   200 成功
	3xx		302重定向    301永久重定向
	4xx   404 路径错误  405 请求方式错误  403 防跨站攻击
	5xx 	500 业务逻辑错误
```

## view视图函数

### 概念及基础语法

```
概念：视图函数MTV中的View，相当于MVC中的Controller作用，控制器 接收用户输入（请求），
	协调模板模型，对数据进行处理，负责的模型和模板的数据交互。
	
视图函数返回值类型：（1）以Json数据形势返回
						前后端分离
						return  json
				 （2）以网页的形势返回    HttpResponse   render   redirect
						重定向到另一个网页
						错误视图(40X,50X)
```

```
url匹配正则注意事项:
					正则匹配时从上到下进行遍历，匹配到就不会继续向后查找了
					匹配的正则前方不需要加反斜线
					正则前需要加 （r）表示字符串不转义
url匹配规则：按照书写顺序，从上到下匹配，没有最优匹配的概念，匹配到就停止了			
			eg：hehe/hehehe
			定义路径结尾都要加上/ 表示完整匹配
```

### 路由参数

```
url接受参数：
          （1）如果需要从url中获取一个值，需要对正则加小括号
                url(r'^grade/(\d+)$',views.getStudents),
                注意，url匹配中添加了 () 取参，在请求调用的函数中必须接收	
                def  getStudents(request,classId)：
                    一个参数
          （2）如果需要获取url路径中的多个参数，那就添加多个括号，默认按照顺序匹配路径名字
                url(r'^news/(\d{4})/(\d)+/(\d+)$',views.getNews),
                匹配年月日 def getNews(request,year,month,day)：
                    多个参数
                eg:def get_time(request,hour, minute, second):
    					return HttpResponse("Time %s: %s: %s" %(hour, minute, second))
          （3）参数也可以使用关键字参数形势
                 url(r'^news/(?P<year>\d{4})/(?P<month>\d)+/(?P<day>\d+)$',views.getNews),
                    多个参数并且指定位置
               eg:def get_date(request,  month, day, year):
   						 return HttpResponse("Date %s- %s- %s" %(year, month, day))
   						 
   		总结路径参数：
                  位置参数
                      使用圆括号包含规则
                      一个圆括号代表一个参数
                      代表视图函数上的一个参数
                      参数个数和视图函数上的参数一一对应（除默认request）
                  关键字参数
                      可以在圆括号指定参数名字 （?P<name>reg）
                      视图函数中存在和圆括号中name对应的参数
                      参数不区分顺序
                      个数也需要保持一致，一一对应
```

```
使用圆括号包裹正则匹配，可以规定参数名：
for example：
1.
	url(r'^testRoute/(\d{5})/(\d+)/',views.testRoute)
	def testRoute(request,vari1,vari2):
		# 对应的参数会获取对应的路由参数。
		return HttpResource('NOT ME')

2. 
	url(r'^testRoute/(?P<id>\d{5})/(?P<number>\d+)/',views.testRoute)
	def testRoute(request,id,number):
		# 对应的参数会获取对应的路由参数。
		return HttpResource('NOT ME')
```

### 内置函数

```
内置函数
	locals()
		将局部变量，使用字典的形式打包
		key是变量的名字
		value是变量的值
```

```
例子：
def testLocal(request):
	name ='老王'
	age=18
	return render(request,'base.html',context = locals())
	
html:
{{ name }}:{{ age }}
```

### 反向解析

```
反向解析
	配置
		在根urls中
              url(r'^views/', include('ViewsLearn.urls',namespace='view')),
                      在根路由中的inclue方法中添加namespace参数
		在子urls中
              url(r'^hello/(\d+)',views.hello,name='sayhello'),
			         在子路由中添加name参数
		在模板中使用
              <a href="{% url 'view:sayhello' %}">Hello</a>

			调用的时候 反向解析的路径不能有编译错误  格式是  {% url 'namespace:name' %}
                        {% url %}
                            {% url 'namespcae:name' %}
		如果存在位置参数
			{% url  ‘namespace:name'   value1 value2 ... %}
		如果存在关键字参数
			{% url 'namespace:name'   key1=value1 key2=vaue2 ...%}
		在模板中使用
			<a href="{% url 'view:sayhello'  year=2017 %}">Hello</a>
	优点
		如果在视图，模板中使用硬编码连接，在url配置发生改变时，需要变更的代码会非常多，这样导致我们的代码结构不是很容易维护，使用反向解析可以提高我们代码的扩展性和可维护性。
```

```
在写根路由的时候最好都给namespace 一个值
写子路由的时候最好也给name一个值

for example：
	
根路由：	url('^base/',include('BaseApp.urls',namespace='base'))
子路由：	url('^testMe',views.testMe,name='testMe')
```

```
试图函数中的反向解析 反向解析：
            		python代码中的反向解析（一般python代码的反向解析都会结合重定向一起使用）
                      reverse('namespace:name')
                      位置参数
                          reverse('namespace:name', args=(value1, value2 ...))
                          reverse('namespace:name', args=[value1, value2 ...])
                      关键字参数
                          reverse('namespace:name', kwargs={key1:value2, key2:value2 ...})
```





作业：完成网页的增删改查功能



### request对象

```
概念：django框架根据Http请求报文自动生成的一个对象，包含了请求各种信息。
属性：
       path：请求的完整路径
       method：GET  1.11版本最大数据量2K
	          POST 参数存在请求体中，文件上传等。
			  请求的方法，常用GET,POST
			  应用场景：前后端分离的底层 判断请求方式 执行对应的业务逻辑
	   GET：QueryDict类字典结构 key-value
		                      一个key可以对应多个值
		                      get 获取最后一个
		                      getlist 获取多个
							类似字典的参数，包含了get请求方式的所有参数
	  POST： 类似字典的参数，包含了post请求方式的所有参数
	  encoding：编码方式，常用utf-8
	  FILES：类似字典的参数，包含了上传的文件  文件上传的时候会使用  
	         页面请求方式必须是post   form的属性enctype=multipart/form-data
	         flask和django通用的   一个是专属于django
	  COOKIES：类似字典的参数，包含了上传的文件  获取cookie
	  session：类似字典，表示会话
	  META：   应用反爬虫  REMOTE_ADDR  拉入黑名单
	           客户端的所有信息 ip
	           print(request.META)
			  for key in request.META:
			        print(key, request.META.get(key))
			  print("Remote IP", request.META.get("REMOTE_ADDR"))
```

```
例子：
GET请求
request.GET.get('name')
	#得到get请求中最后一个name的值
request.GET.getlist('name')
	#得到一个列表，存储name的多个值
	
POST请求
request.POST.get('name')
	#得到post请求中name的值，post多为form表单发送数据
request.POST.getlist('name')
	#得到多个name的值

path
path = request.path
	#得到请求的完整路径,不包括域名，不包括get请求参数

method
method = request.method
	#得到请求的方法

encoding
encoding = request.encoding 默认是None

FILES
file = request.FILES
	#得到一个MultiValueDict的对象，没得参数即为{}

META
META中有很多值，默认是键值对形式输出。
meta_addr = request.META.get('REMOTE_ADDR')
	#其中remote_addr是获取主机地址

cookie
session
We will talk them later.
```

### HttpResponse对象

#### 1.HTML响应



##### html响应：

```
（1）基类HttpResponse   不使用模板，直接HttpResponse()
	def hello(request):
             response = HttpResponse()
             response.content = "德玛西亚"
             response.status_code = 404
             response.write("千锋")
             response.flush()
        return response
     方法
		 init				初始化内容
	     write(xxx)			直接写出文本
         flush()				冲刷缓冲区
         set_cookie(key,value='xxx',max_age=None,exprise=None)
         delete_cookie(key)		删除cookie，上面那个是设置
```

```
HttpResponse是最基本的类，所有响应都是继承自它。
```

#####  render

```
（2）render转发：
		方法的返回值类型也是一个HttpResponse
```

```
例子：
def index(request):
	context = {'name':'Lucy',}
	return render(request,'base.html',context=context)
# 内容一定是一个字典，并且可以josn序列化。
```

##### redirect

```
（3）HttpResponseRedirect重定向
     HttpResponse的子类，响应重定向:可以实现服务器内部跳转
	return HttpResponseRedict('/grade/2017')使用的时候推荐使用反向解析
	
	状态码：302
	
	简写方式：简写redirect方法的返回值类型就是HttpResponseRedirect
	
```

```
例子：
重定向：302
return HttpResponseRedirect(reverser('namespace:name',args=(vari1,vari2……，kwargs={k1:v1,k2:v2,k3:v3……})))
其中namespace是在根路径中include的参数，而name是子路径中name的参数,args是不定参数，可以使用圆括号()或者方括号[]包裹。kwargs是字典形式，也是关键字参数

永久重定向：301
return HttpResponsePermanentRedirect('namespace:name',args=(vari1,vari2……，kwargs={k1:v1,k2:v2,k3:v3……})))
	#参数同上

重定向简写：
return redirect('namespace:name',args=[vari1,vair2,……],kwargs={k1:v1,k2:v2,……})

```



#### 2.JsonResponse（前后端分类）

```
这个类是HttpRespon的子类，它主要和父类的区别在于：
1.它的默认Content-Type 被设置为： application/json

2.第一个参数，data应该是一个字典类型，当 safe 这个参数被设置为：False ,那data可以填入任何能被转换为JSON格式的对象，比如list, tuple, set。 默认的safe 参数是 True. 如果你传入的data数据类型不是字典类型，那么它就会抛出 TypeError的异常。

def get_info(request):
	data = {
        "status": 200,
        "msg": "ok",
    }
	return JsonResponse(data=data)
```



#### HttpResponse的子类总结：

```
HttpResponse子类
	HttpResponseRedirect 
		-302
	HttpResponsePermanentRedirect
		- 重定向，永久性- 
		-301
	HttpResponseBadRequest	
		-400
	HttpResponseNotFound
		- 404
	HttpResponseForbidden
		- 403   csrf 防跨站攻击 
	HttpResponseNotAllowed
		- 405   
	HttpResponseServerError
		- 500
	Http404- Exception
           - raise 主动抛异常出来
```

### 会话技术：cookie和session

```
为什么会有会话技术？
	服务器如何识别客户端
	Http在Web开发中基本都是短连接
	请求生命周期从Request开始，到Response就结束
会话技术：cookie session  token（自定义的session）
```

#### cookie

```
	客户端会话技术，数据都存储在客户端，以key-value进行存储，支持过期时间max_age，默认请求会携带本网站的所有cookie，cookie不能跨域名，不能跨浏览器，cookie默认不支持中文base64
	cookie是服务器端创建  保存在浏览器端
	设置cookie应该是服务器 response
	获取cookie应该在浏览器 request
	删除cookie应该在服务器 response
cookie使用：
	设置cookie：response.set_cookie(key,value）
	获取cookie：username =request.COOKIES.get("username")
	删除cookie：response.delete_cookie("content")
	
	可以加盐：加密 获取的时候需要解密
		加密  response.set_signed_cookie('content', uname, "xxxx")
		解密  
			 获取的是加盐之后的数据
			 	uname = request.COOKIES.get('content)
			 获取的是解密之后数据
			 uname = request.get_signed_cookie("content", salt="xxxx")
		
	通过Response将cookie写到浏览器上，下一次访问，浏览器会根据不同的规则携带cookie过来
		max_age:整数，指定cookie过期时间  单位秒
		expries:整数，指定过期时间，还支持是一个datetime或	timedelta，可以指定一个具体日期时间
		max_age和expries两个选一个指定
		过期时间的几个关键时间
			max_age 设置为 0 浏览器关闭失效
			设置为None永不过期
			expires=timedelta(days=10) 10天后过期
```

```
例子：
def setCookie(request):
    response = redirect(reverse('response:getCookie'))
    try:
        name = request.POST.get('name')
        # response.set_cookie('h1', bytes('你好', 'utf-8').decode('ISO-8859-1'))
        name = bytes(name, 'utf-8').decode('iso-8859-1')
        response.set_cookie('name', name)
    except:
        print('错误')

    return response

def welcome(request):
    # name = request.COOKIES.get('name', '游客')
    try :
        name = request.COOKIES.get('name').encode("iso-8859-1").decode('utf8')
    except:
        name = ''
    if name:
        pass
    else:
        name = '游客'
    return render(request, 'welcome.html', context=locals())

def login(request):
    return render(request, 'login.html')

def logout(request):
    response = redirect(reverse('response:getCookie'))
    response.delete_cookie('name')
    return response

#！！！cookie默认是不能存储中文的，使用base64
```

#### session

```
	服务端会话技术，数据都存储在服务端，默认存在内存 RAM，在django被持久化到了数据库中，该表叫做Django_session,这个表中有三个字段，分别为seesion_key,session_data,expris_date.
	Django中Session的默认过期时间是14天，支持过期，主键是字符串，默认做了数据安全，使用了BASE64
		- 使用的base64之后 那么这个字符串会在最后面添加一个=
		- 在前部添加了一个混淆串
	依赖于cookies
session使用：
	设置session
		    request.session["username"] = username
	获取session
		    username = request.session.get("username")
	使用session退出
            del request.session['username']
                cookie是脏数据
            response.delete_cookie('sessionid')
                session是脏数据
            request.session.flush()
			冲刷
	session常用操作
		get(key,default=None) 根据键获取会话的值
		clear() 清楚所有会话
		flush() 删除当前的会话数据并删除会话的cookie
		delete request['session_id'] 删除会话
		session.session_key获取session的key
		request.session[‘user’] = username
			数据存储到数据库中会进行编码使用的是Base64
```

```
例子：
def toLogin(request):
    return render(request, 'session_login.html')

def setSession(request):
    name = request.POST.getlist('name')
    response = redirect(reverse('session:WelcomeSession'))
    request.session['name'] = name[0]
    return response

def WelcomeSession(request):
    name = request.session.get('name', '游客')
    context = {
        'name': name,
    }
    return render(request, 'session_welcome.html', context=context)

def logout(request):
    response = redirect(reverse('session:WelcomeSession'))
    try:
        # del request.session['name']  # cookie还在
        # request.delete_cookie('sessionid') # session还在
        
        # cookie 和session都删干净
        request.session.flush() 
    except:
        pass
    return response
```

#### token

```
基本概念：Token 的中文意思是“令牌”。主要用来身份验证。 Facebook，Twitter，Google+，Github 等大型网站都在使用。比起传统的身份验证方法，Token 有扩展性强，安全性高的特点，非常适合用在 Web 应用或者移动应用上,如果使用在移动端或客户端开发中，通常以Json形式传输，服务端会话技术,自定义的Session,给他一个不能重复的字符串,数据存储在服务器中
```

```
验证方法：使用基于 Token的身份验证方法，在服务端不需要存储用户的登录记录。大概的流程是这样的：
1.客户端使用用户名跟密码请求登录
2.服务端收到请求，去验证用户名与密码
3.验证成功后，服务端会签发一个 Token，再把这个Token 发送给客户端
4.客户端收到 Token以后可以把它存储起来，比如放在 Cookie里或者 Local Storage里
5.客户端每次向服务端请求资源的时候需要带着服务端签发的Token
6.服务端收到请求，然后去验证客户端请求里面带着的 Token，如果验证成功，就向客户端返回请求的数据
```

```

python常用Token生成方法：
（1）binascii.b2a_base64(os.urandom(24))[:-1]
	使用举例：
		>>> import binascii
		>>> import os
		>>>binascii.b2a_base64(os.urandom(24))[:-1]

		b'J1pJPotQJb6Ld+yBKDq8bqcJ71wXw+Xd'
	总结：这种算法的优点是性能快， 缺点是有特殊字符， 需要加replace 来做处理。
（2）sha1(os.urandom(24)).hexdigest()
	使用举例：
		>>> import hashlib
		>>> import os
		>>> hashlib.sha1(os.urandom(24)).hexdigest()

		'21b7253943332d0237a720701bcb8161b82db776'
	总结：这种算法的优点是安全，不需要做特殊处理。缺点是覆盖范围差一些。
 （3）uuid4().hex
 	使用举例：
 		>>> import os
		>>> import uuid
		>>> uuid.uuid4().hex

		'c58a80d3b7864b0686757b95e9626e47'
	总结：Uuid使用起来比较方便， 缺点为安全性略差一些。
（4）base64.b32encode(os.urandom(20))/base64.b64encode(os.urandom(24))
	使用举例：
		>>> import base64
		>>> import os
		>>>base64.b32encode(os.urandom(20))
		
		b'NJMTBMOYIXHNRATTOTVONT4BXJAC25TX'
		
		>>>base64.b64encode(os.urandom(24))

		b'l1eU6UzSlWsowm8M8lH5VaFhZEAQ4kQj'
	
	总结：可以用base64的地方，选择binascii.b2a_base64是不错的选择
		 根据W3的SessionID的字串中对identifier的定义，SessionID中使用的是base64，但在Cookie的值内使用需要注意“=”这个特殊字符的存在；
		 如果要安全字符（字母数字），SHA1也是一个不错的选择，性能也不错；
```

```
token的应用：
import hashlib

# 待加密内容
strdata = "xiaojingjiaaseafe16516506ng"

h1 = hashlib.md5()
h1.update(strdata.encode(encoding='utf-8'))

strdata_tomd5 = h1.hexdigest()

print("原始内容：", strdata, ",加密后：", strdata_tomd5)

import time
import base64
import hmac


# 生产token
def generate_token(key, expire=3600):
    r'''''
        @Args:
            key: str (用户给定的key，需要用户保存以便之后验证token,每次产生token时的key 都可以是同一个key)
            expire: int(最大有效时间，单位为s)
        @Return:
            state: str
    '''
    ts_str = str(time.time() + expire)
    ts_byte = ts_str.encode("utf-8")
    sha1_tshexstr = hmac.new(key.encode("utf-8"), ts_byte, 'sha1').hexdigest()
    token = ts_str + ':' + sha1_tshexstr
    b64_token = base64.urlsafe_b64encode(token.encode("utf-8"))
    return b64_token.decode("utf-8")


# 验证token
def certify_token(key, token):
    r'''''
        @Args:
            key: str
            token: str
        @Returns:
            boolean
    '''
    token_str = base64.urlsafe_b64decode(token).decode('utf-8')
    token_list = token_str.split(':')
    if len(token_list) != 2:
        return False
    ts_str = token_list[0]
    if float(ts_str) < time.time():
        # token expired
        return False
    known_sha1_tsstr = token_list[1]
    sha1 = hmac.new(key.encode("utf-8"), ts_str.encode('utf-8'), 'sha1')
    calc_sha1_tsstr = sha1.hexdigest()
    if calc_sha1_tsstr != known_sha1_tsstr:
        # token certification failed
        return False
        # token certification success
    return True


key = "xiaojingjing"
print("key：", key)
user_token = generate_token(key=key)

print("加密后：", user_token)
user_de = certify_token(key=key, token=user_token)
print("验证结果：", user_de)

key = "xiaoqingqing"
user_de = certify_token(key=key, token=user_token)
print("验证结果：", user_de)
```



#### cookie和session的区别

```
1、cookie数据存放在客户端上，session数据放在服务器上。
2、cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗 
考虑到安全应当使用session。
3、session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能 
考虑到减轻服务器性能方面，应当使用COOKIE
```



#### session与token的区别

```
1.作为身份认证 token安全性比session好，因为每个请求都有签名还能防止监听以及重放攻击
2.Session 是一种HTTP存储机制，目的是为无状态的HTTP提供的持久机制。Session 认证只是简单的把User 信息存储到Session 里，因为SID 的不可预测性，暂且认为是安全的。这是一种认证手段。 但是如果有了某个User的SID,就相当于拥有该User的全部权利.SID不应该共享给其他网站或第三方.
3.Token,如果指的是OAuth Token 或类似的机制的话，提供的是 认证 和 授权 ，认证是针对用户，授权是针对App。其目的是让 某App有权利访问 某用户 的信息。这里的 Token是唯一的。不可以转移到其它 App上，也不可以转到其它 用户上。
```

### csrf豁免

```
CSRF
	防跨站攻击
	实现机制
		页面中存在{% csrf_token %}时
		在渲染的时候，会向Response中添加 csrftoken的Cookie
		在提交的时候，会被添加到请求体中， 会被验证有效性
    csrf（https://www.jianshu.com/p/d1407591e8de）
解决csrf的问题/csrf豁免：
    1 注释中间件
    2 在表单中添加{%csrf_token%}
    3 在方法上添加 @csrf_exempt
    
    建议使用html表单form中加
    {% csrf_token %}
    这会产生一个hidden标签，传递一个唯一值。
```

### 模型迁移

#### models.py迁移到database（mysql）

```
Model -> DB
          迁移步骤
              生成迁移文件  python manage.py makemigrations
              执行迁移文件  python manage.py migrate
          迁移文件的生成
              根据models文件生成对应的迁移文件
              根据models和已有迁移文件差别 生成新的迁移文件
          迁移原理  了解
              先去迁移记录查找，哪些文件未迁移过
                  app_label + 迁移文件名字
              执行未迁移的文件
              执行完毕，记录执行过的迁移文件
          可以指定迁移的app  python manage.py makemigrations app
                            python manage.py migrate    
          重新迁移
              删除迁移文件
                  migrations所涉及的迁移文件
              删除迁移文件产生的表
              删除迁移记录
                  django-migrations

删除迁移记录：
 删除migrations文件夹中的迁移文件.py	
 删除数据库中models生成的表
 删除数据库表django_migrations 中迁移App的记录
 
 不想
```

#### database（mysql）迁移到medels

```
DB -> Model
	反向生成到指定得app下 --》  python manager.py inspectdb > App/models.py
	元信息中包含一个属性  managed=False   不支持迁移
	- 如果自己的模型不想被迁移系统管理，也可以使用 managed=False进行声明
	
insepectdb会迁移当前连接数据库中所有的表，产生模型。
```



### 模型关系

#### 一对一 OneToOne

```
应用场景
	用于复杂表的拆分
	扩展新功能
	OneToOneField
	确认主从关系，谁声明关系谁就是从表
	底层实现，使用外键实现的，对外键添加了唯一约束

关键语句： 
	定义字段时：
		id_student = models.OneToOneField (Student，null=True,blank=True ,on_delete =models.SET_NULL)

#其中on_delete的默认值默认是None，也就是cascade。这样在删除主表时，从表的数据也会跟着删除掉。
```

```
例子：
class Student(models.Model):
    student_name = models.CharField(max_length=32)
    student_age = models.IntegerField(default=0)
    class Meta:
        db_table = 'student'
	

class IdCard(models.Model):
    id_number = models.IntegerField()
    id_studeng = models.OneToOneField(Student, null=True, blank=True, on_delete=models.SET_NULL)
	class Meta():
        db_table = 'idcards'
```

```
增加数据：
def addStudent(request):
    student = Student()
    student.student_name = '老王'
    student.student_age = 18
    student.save()
    return HttpResponse('加上了')

def addId(request):
    card = IdCard()
    card.id_number = 2016305036
    card.save()
    return HttpResponse('好了')
    
绑定两个表
def bindthem(request):
	student =Student.object.first()
	idcard = IdCard.object.first()
	card.id_studeng = student
    card.save()
    return HttpResponse('好嘞')
```

```
删除从表：
def deleteId(request):
    id =IdCard.objects.first()
    id.delete()
    return HttpResponse('删特了')
    
#直接删就行了。
```



```
删除主表：cascade：
def deleteStudent(request):
    student =Student.objects.first()
    student.delete()
    return HttpResponse('么得了')
    
删除语句就这么一个，但是models中的参数不同，结果也不同。
    id_studeng = models.OneToOneField(Student, null=True, blank=True, on_delete=models.CASCADE)
# 定义字段的语句是这个，那么删除就是级联的，主表数据和从表对应数据一起删除

    id_studeng = models.OneToOneField(Student, null=True, blank=True, on_delete=models.SET_NULL)
# 差别在于on_delete=models.SET_NULL， 参数为这个值，那么在删除主表时，从表的外键字段会设为null

    id_studeng = models.OneToOneField(Student, null=True, blank=True, on_delete=models.PROTECT)
# on_delete=models.PROTECT需要先删从表，不然主表删不掉，会报错。
```



#### 一对多 ForeignKey

```python
# 部门表
class Departement(models.Model):
    d_name = models.CharField(max_length=32)
    class Meta:
        db_table = 'dept'
# 员工表
class Emplo(models.Model):
    e_name = models.CharField(max_length=32)
    e_age = models.IntegerField()
    e_dept = models.ForeignKey(Departement, null=True, blank=True, on_delete=models.SET_NULL)
    # 一对多使用外键，而不是onetomany
    class Meta:
        db_table = 'emplooyee'
```



添加（同时建立连接）

注意：`当主表数据提交后才能在从表中建立外键`

```python
def add(request):
    emp1 = Emplo()
    emp1.e_name = 'tom'
    emp1.e_age = 18

    emp2 = Emplo()
    emp2.e_name = 'jerry'
    emp2.e_age = 18

    dept = Departement()
    dept.d_name = '销售部'

    dept.save()
    
    emp2.e_dept = dept
    emp1.e_dept = dept
    
    emp1.save()
    emp2.save()
    # emp1 和emp2 保存应该在部门已经存在的前提下，不然外键会不能提交
    return HttpResponse('加好了')
```

删除

注意：`删除基于查询，只有得到查询对象才能进行删除。`

```
def delete(request):
    dept = Departement.objects.filter(d_name='研发部门')
    dept.delete()
    return HttpResponse('删掉了')
```

查询

主查从：

```python
def querykey(request):
    dept = Departement.objects.filter(d_name='人力资源')[0]
    emp_list = dept.emplo_set
    # set集后面不能出现括号，需要所有结果，又需要.all() 才能得到queryset
    for ind in emp_list.all():
        print(ind.id, ind.e_name, ind.e_age)
    print(dept.d_name)
    return HttpResponse('查到了')
```

从查主:

```python
def queryfor(request):
    emp = Emplo.objects.filter(e_name='zs')
    deptment = emp[0].e_dept
    print(deptment.id, deptment.d_name)
    return HttpResponse('查到了')
```

#### 多对多 manytomany

```

```
















































​																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																										