# javascript学习

##js定义

JavaScript是一种小型的、轻量级的、面向对象的、跨平台的客户端脚本语言。

JavaScript一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型。

## js的功能

**JavaScript的六大作用：**

- 直接在script输出
- 对事件做出反应
- 改变html的内容
- 改变html的图像
- 改变html的样式
- 验证输出

##js特性

1. 脚本语言
2. 基于对象
3. 简单
4. 动态性
5. 跨平台性

## js的输出方式

```javascript
document.write();//在html中的body写
window.alert();//弹出通知，多用于警告
console.log();//在浏览器检查中的console窗口查看，多用于调试程序
```

## js注释

```javascript
js的注释：// 单行注释
		/*多行注释*/
css中的注释：/*多行*/
html中的注释：<!--多行-->
```



##js中的变量

###js变量声明

使用关键字`var`声明变量

变量命名规则通用（与python一致）。

需要注意的是$也可以用，但是不建议，有特殊意义。

### js变量的数据类型

基本类型：字符型，数值型（包含整型，浮点型，NaN），boolean（布尔型），未定异型（undefined），空（null）

复合类型：数组型（类似list），对象型（类似dict），函数型（function）。

**在js中字符串和数值是可以使用加号+运算的，作用是拼接（自动把数值转换成字符串）**

**变量是没有类型，只有变量的值才有类型**

####数值型Int、Float、NaN

数值型包含：整形，浮点型，NaN（not a number）

在转换类型的时候只有以数字开头的数据都能转成整型和浮点型。（其他字符开头的不能转为Int，Float）parseInt(variable),parseFloat(variable)

toFixed(n)，保留n位小数

#### 字符串String

字符串就是有引号包裹的值，'' "" 

在转换为字符时原型转换，只是在两边加上引号。String(variable)

length属性,得到长度。

toLowerCase()，字符串转为全小写.

toUpperCase()，字符串转为全大写.

charAt(index)，查询对应下标处的字符。

indexOf(str)，从左边查找str在原字符串的位置，只找一次，找不到返回-1。

lastIndexOf(ste)，从右边查找str在原字符串的位置，只找一次，找不到返回-1。

substr(n,m)，返回字符串，从下标n处取出m个字符

substring(x,y)，返回字符串，从下标x处取到y处，x、y是非负整数，前后顺序无所谓。

split(str),切割字符串，以str为切割对象，返回一个数组。



####布尔型Boolean

只有true和false两个值。

在类型转换的时候：

有值的类型才能转成true（除了0）

零和没值的类型都会转成false（NaN,null,undefined,""）

####未定义型undefined

####空null

####数组

数据相当于python中的list，在js中叫array。

数组元素可以通过索引（下标）添加和修改，可以通过delete和索引删除元素（位置依然保留，值变成undefined）。

数组有属性length表示数组的长度。

以上操作实现：

```javascript
var arr = new Array();
arr[0] = 1;//没有就添加值，有就修改
delete arr[0] //删除值，位置保留
arr.length //此时长度依然是1
```

数组的嵌套实现多维数组。

```javascript
var arr = [            
  [10,11,12,13],
  [20,21,22],
  [30,31],
  [40]
]
//二维数组
```

length属性，返回数组长度。

join(char)，使用char连接数组，返回一个数组

shift()，删除数组第一元素。

pop()，删除数组最后一个元素。

unshift()，在开头增加多个元素，使用逗号隔开。

push()，数组结尾增加多个元素，使用逗号隔开。

reverse()，逆序数组。



#### 函数

使用function关键字定义，用法与python差不多，只是没有yield关键字了。

#### 对象

相当于python中的dict，属于键值对。

```javascript
var ob = new Object();
ob.name = '刘哥'
console.log(ob.name)
//键值对的形式存储
//调用使用点 object对象.key 
```

## 内置对象

String对象，字符串。

Array对象，数组。

Boolean对象，布尔。

Number对象，数值。

Math对象，数学方面的属性和方法。

Date对象，日期。

###日期对象Date

```javascript
var d = new Date();
//也可以加上某个日期时间。
var da = new Date(2017/4/3 13:23:1);
da.getTime();//得到时间戳

var dat = new Date(2019-1-1 0:1:1);
dat.getMonth();//得到月份

var date = new Date(2011,2,3,16,24,24);
date.getSeconds();//得到秒数
```

getFullYear()  返回年份

getMonth() 月

getDate() 日

getHours() 小时

getMinutes() 分钟

getSeconds() 秒钟

getMilliseconds() 毫秒

getDay() 星期几，0-6，从星期天开始

getTime() 获取时间戳，毫秒

###Math数学对象

Math对象，数学方面的属性和方法。

定义方法：

```javascript
var mat = Math;
```

PI 属性，圆周率。

abs()，绝对值

ceil()，向上取整。

floor()，向下取整。

round()，四舍五入。

pow()，做幂运算。

sqrt()，开方。

random()，随机取0~1的小数。













##js中的运算符

js有++ 表示自增1，-- 自减1。

b = a++先赋值再运算,b = ++a线运算再赋值。

--同理。

### 逻辑运算符

&&且，||或，！非

### new运算符

实例化对象。

```javascript
var today = new Date();
```

### delete运算符

删除对象的属性或数组中的元素。

```javascript
var obj = {a:1,b:2};
console.log(obj);
delete obj.a
```

### typeof运算符

判断一个变量的类型

```javascript 
描述：一元运算符typeof，是判断变量的数据类型的。

语法：typeof name  或  typeof(name)

返回值：它返回六种字符串型的数据类型。包括： “string”、“number”、“boolean”、“object”、“function”、“undefined”,'null','array'
```

### 小数点 . 

实现调用的运算符。

###括号（）、[ ]

() 运算符：主要用优先级方面。也是方法参数的小括号，函数参数小括号。

[ ] 运算符：主要用于存取数组中的元素。

## 判断

if 判断语法形式：

```javascript
if (){}
else if (){}
……
else {}

```

switch判断语句：

```javascript
switch(条件判断,是一个变量的不同取值){
	case 值1:
  	  代码1;
  	  break;
	case 值2:
  	  代码2;
  	  break;
	case 值3:
  	  代码2;
  	  break;
	default:
  		如果以上条件都不满足,则默认执行的代码
}
//switch使用 ===全等于 判断
```



## 循环

for循环：

```javascript
for ( var i=0; i <10;i++){
    
}
for (i in 数组或字符串){
    
}
```



while循环：

```javascript
while(条件){
      //与python差不多
      }
```

### 破坏当前循环

break，直接退出当前循环。

continue，回到条件判断，continue后的语句执行。





#BOM

Browers Object Model 浏览器对象模型

BOM只是一个标准，是一个模型，是一个概念。它不是真正能操作的对象。

window 浏览器窗口

location 地址栏对象

history 历史记录对象

screen 屏幕对象

navigator 浏览器软件对象



## window

浏览器可视窗口，指整个浏览器。

```javascript
window.alert()//警告或称通知对话框，只有一个按钮。
window.prompt()//弹出输入对话框，确认返回字符串，取消返回null。
window.confirm()//确认对话框，确认返回true，取消返回false
window.close() // 关闭窗口
window.open() //打开新窗口
open参数：
url：在新窗口中打开的文件的URL地址，可以为空。

name：新窗口的名字。可以通过window.name属性来获取，用于<a>标记的target属性。

options：新窗口的规格。

menubar：是否显示菜单栏，取值：yes、no

toolbar：是否显示工具栏。

status：是否显示状态栏。

scrollbars：是否显示滚动条。

location：是否显示地址栏。

width：新窗口的宽度

height：新窗口的高度

left：新窗口距离屏幕左边距离。

top：新窗口距离屏幕顶边距离。
```

## document

文档窗口，指主体内容。

```javascript
document.write()//在body中写入
document.getElementById('id')
```



## screen

width 屏幕总宽度

height 屏幕总高度

availWidth 屏幕有效宽度

availHeight 屏幕有效高度

```javascript
screen.width;
```



## navigator

appName 浏览器软件名

appVersion 浏览器软件版本号，是核心版本号

systeLanguage 系统语言

userLanguage 用户语言

platform 平台



##location

href：获取或设置地址栏中的地址。如：location.href = “http://www.sina.com.cn”

host 获取或设置主机名

hostname 主机名

pathname 文件及路径

search 查询字符串

protocol 协议

hash 锚点名称

reload 刷新

## history

go() 进或退

```javascript
history.go(0) //刷新
history.go(1) //进一步
history.go(2) //进二步
history.go(-1) //退一步
history.go(-2) //退二步

```

forward() 相对于“前进”按钮

back() 相当于“后退”按钮







# DOM

Document Object Model

#延时器

只执行一次

```javascript
var timer = window.setTimeout(func,1000)
var time = window.setTimeout('func()',1000)
//两种方式都是定义一个延时器，1000的单位是毫秒

window.clearTimeout(timer)
//清除timer延时器
```



window.setTimeout(variable,millisecond)

window.clearTimeout(variable)

# 定时器

周期性执行

```javascript
var time1 = window.setInterval(func,1000)
var time2 =window.setInterval('func()',1000)

window.clearInterval(time1)
```



window.setInterval(variable,millisecond)

window.clearInterval(ele)







## js查找元素常用的方法

1. 通过id查找

```javascript
document.getElementById('id')
```



2. 通过name查找

```javascript
document.getElementByName('name')
```



3. 通过元素名查找

```javascript
document.getElementsByTagName('tagname')
```

……





## js的安全性

1. JavaScript不允许读写客户机器上的文件。这是有好处的，因为你肯定不希望网页能够读取自己硬盘上的文件，或者能够将病毒写入硬盘，或者能够操作你的计算机上的文件。唯一例外是，JavaScript可以写到浏览器的cookie文件，但是也有一些限制。
2. JavaScript不允许写服务器机器上的文件。尽管写服务器上的文件在许多方面是很方便的（比如存储页面点击数或用户填写表单的数据），但是JavaScript不允许这么做。相反，需要用服务器上的一个程序处理和存储这些数据。这个程序可以是Perl或者PHP等语言编写的CGI运行在服务器上的程序或者Java程序
3. JavaScript不能关闭不是它自己打开的窗口。这是为了避免一个站点关闭其他任何站点的窗口，从而独占浏览器。
4. JavaScript不能从来自另一个服务器的已经打开的网页中读取信息。换句话说，网页不能读取已经打开的其它窗口中的信息，因此无法探查访问这个站点冲浪者还在访问其它哪些站点。　

详情：aug8/aug15-aug8/aug15。js学习，周四-周五。









