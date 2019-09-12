#html学习

##html超文本标注语言

HTML：hyptertext Markup Language

超文本标注语言

超文本：除了文本以外，还可能有图片、音乐、视频、链接等。
标注：可以理解为一种“标记”“记号”“标志”。如：交通标志。如：`<font>Python</font>`
语言：这里的语言与程序半点关系都没有。

##B/S网络结构

browser / server 浏览器/服务器

##html文件结构树

```html
<!document>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <title>标题</title>
    </head>
<body>
</body>
</html>
<!--基本的html文件结构-->
```

## html标签

### 标签格式

1. 双边标记

```html
<tagname 属性="属性值" ……>内容</tagname>
```

2. 单边标记

```html
<tagname 属性="属性值"/>
```

### 标签书写规范

html语言不区分大小写。

标签可以省略属性，自动调用默认值。

多属性间使用空格隔开。

标签嵌套只能顺序嵌套，不能交叉。

###文本

```html
<b></b>文本加粗(bold)。
<i></i>文本斜体(italic)。
<u></u>下划线(underline)。
<s></s>删除线(strike)。
<sup></sup>上标。
<sub></sub>下标。
<font></font>文本字体。
color：文本颜色。
size：文字大小，取值1-7。1小，7大。
face：字体样式。取值：黑体、楷体、Arial、……

```

### 排版

```html
<p>
    段落标记，前后空行，常用属性：align。
</p>
<br/> 换行符
<hr/> 水平线 常用属性：
color：线条颜色。
size：线的粗细
width：线的宽度
align：线的水平对齐方式，取值：left、 	    center、right
noshade：是否要去阴影。该属性没有值。
<pre>
预排版标记，保留输出空白字符。
</pre>
<h1>标题标签，h1是大标题，h1直到h6</h1>
```

### 块元素和行内元素

```html
<div>
    本身没意义，但是排版占据一行，用来排版。
</div>
<span>
    本身没有宽度，宽度决定于其中的内容</span>

```

### 字符实体

```html
空格：&nbsp; (一个汉字占用两个空格的空间)
<：&lt;
>：&gt;
&：&amp;
版权号：&copy;
￥：&yen;
×：&times;
÷：&divide;
```

###无序列表

```html
<ul>
    <li>列表第一行</li>
    <li>列表第二行</li>
    ……
常用属性：type：项目符号的类型，取值：disc(小黑点)、circle(圆圈)、square(小方块)
</ul>
```

###有序列表

```html
<ol>
    <li>列表第一行</li>
    <li>列表第二行</li>
    ……
</ol>
```

###自定义列表

```html
<dl>
    <dt>一级标题</dt>
    	<dd>一级标题内容</dd>
    <dt>二级标题</dt>
    	<dd>二级标题内容</dd>
    ……
</dl>
```

### 滚动字幕

```html
<marquee direction='left' width='400px' height='300px' bgcolor='#ffff66' scrollAmount='100' scrollDelay='40'>
<p>我是漂浮物</p>
</marquee>
```

### 图片

```html
<img 属性="属性值" />
属性：
src：指图片的路径，该路径可以是相对地址，也可以是绝对地址。
width：图片的宽度。
height：图片的高度。
alt：图片说明。当图片不存在时，显示一个提示信息。
border：图片边框的粗细。
left或right：可以实现图文混排。
left或right的功能相当于CSS中的“浮动”效果。
```

### 超链接

```html
<a  属性 = “属性值”>链接内容</a>
属性：
href：链接的地址。该地址可以是绝对路径，也可以是相对路径。
target：链接的目标文件在哪个窗口中来打开。
		_blank：弹出一个空白窗口来打开文件。
		_self：在当前窗口中来打开目标文件。
		_parent：在父窗口中来打开目标文件。(常用于框架网页中)
		_top：在最顶层窗口中来打开目标文件。(常用于框架网页中)
name：指定一个锚点名称。所谓“锚点”用于长网页当中。
```

###锚点

```html
<a  name = “top”></a>
省略文件名：
<a  href = “#top”>返回顶部</a>
不省略文件名：
<a  href = “index.html#top”>返回顶部</a>
文件名可以省略。如果省略，跳转到当前网页的那个记号处。
```

###meta

###类型、字符集、自动刷新、关键字、描述

```html
设置网页的类型和字符集：
#h4
<meta http-equiv='Content-Type' content='text/html;charset=utf-8'>

网页字典刷新：
<meta http-equiv="refresh" content="2">   //每隔2秒，刷新网页一次
<meta http-equiv="refresh" content="5;url=http://www.ifeng.com">  //5秒钟后，跳转到凤凰网

设置网页关键字：
<meta name="keywords" content="网站建设，企业网站建设，网站制作，网上商城，网站推广，域名注册，大把推，高端设计定制，企业邮箱，中企动力" />

设置网页描述：
<meta name="description" content="网站建设、网站制作专家中企动力，为您提供专业的展示型网站建设、营销型网站建设、独立商城系统网站建设、汽车4S行业解决方案、社会化">

```

### 表格标签

```html
<table>
    <caption>表格标题</caption>
    <TR><!--tr表示行，内容会在table标签后显示-->
    	<td>第一行第一列</td>
        <th>第一行第二列，自动加粗，居中</th>
    </TR>
</table>
table属性：
border：边线粗细。
bordercolor：边线颜色。
width：表格宽度。
height：表格高度。
align：水平对齐方式，取值：left、center、right
bgColor：背景颜色
background：背景图片
rules：合并所有单元格边线。取值：all
cellpadding：内填充距离(单元格边线到内容间的距离)
cellspacing：单元格间距(两个单元格边线之间的距离)
tr属性：
height：行高。
bgColor：背景色
background：背景图片
align：水平对齐方式，取值：left、center、right
valign：垂直对齐方式，取值：top、middle、bottom
td或th属性：
width：单元格宽度。
height：单元格高度。
bgColor：背景色
background：背景图片
align：水平对齐方式
valign：垂直对齐方式
colspan：合并列的单元格。
rowspan：合并行的单元格。
```

### 音频

audio是H5的新标签

```html
<audio src="路径" controls="controls">
Your browser does not support the audio element.
</audio>
audio的属性:
autoplay='autoplay'	如果出现该属性，则音频在就绪后马上播放.
controls='controls'	如果出现该属性，则向用户显示控件，比如播放按钮。
loop='loop'			如果出现该属性，则每当音频结束时重新开始播放。
preload='preload'	如果出现该属性，则音频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略该属性。
src='url'			要播放的音频的 URL。
```

###视频

video是H5的新标签

```html
<video src="路径" controls="controls">
your browser does not support the video tag
</video>
video的属性:
autoplay='autoplay'		如果出现该属性，则视频在就绪后马上播放。
controls='controls'		如果出现该属性，则向用户显示控件，比如播放按钮。
height='px'		设置视频播放器的高度。
loop='loop' 	如果出现该属性，则当媒介文件完成播放后再次开始播放。
preload='preload' 	如果出现该属性，则视频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略该属性。
src='url' 	要播放的视频的 URL。
width='px' 	设置视频播放器的宽度。
```

### 动画flash

```html
<object classid="name" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,29,0" width="778" height="202">
    <param name="movie" value="../../resource/banner.swf">
    <param name="quality" value="high">
    <param name="wmode" value="transparent">
    <embed src="images_2/banner.swf" width="100%"  quality="high" pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash" wmode="transparent"></embed>
</object>
embed的属性:
height='px'	设置嵌入内容的高度。
src='url'	嵌入内容的 URL。
type='application/x-shockwave-flash'	定义嵌入内容的类型。
width='100'	设置嵌入内容的宽度。
```

### 表单

表单主要用来获取用户数据的。

表单的工作原理:

> 填写有表单的网页，单击某个按钮提交表单。
> 服务器上有专门的程序(Python程序或者其他PHP语言)，对提交的表单数据进行验证。
> 如果验证通过，服务器会返回一个成功的消息。
> 如果验证失败，服务器会返回一个失败的消息。

```html
<form enctype="multipart/form-data" action="http://www.xxxx.com/path" name="login"  method="post"  >
	<span>用 户 名 : </span><input type="text" name="username"  value="" placeholder='请输入账号'/>
    <br/>
	<span>登录密码:</span><input type="password" name="pwd"  value="" placeholder='请输入密码'/>
    <br/>
	<input type="submit" name="submit"   value="登录" disabled />
</form>
表单form的属性：
name：表单名称。用来区分不同的表单，JS可以通过name的值，对表单进行前端的验证。
method：表单数据的发送方式，取值：get和post
action：指定表单数据的处理程序。一般是服务器端的脚本程序(PHP/Python)。如果为空，则提交给自己来处理。
enctype：表单数据的一个加密(编码)方式。enctype属性只能在 method = post 的表单中。
```

GET提交方法的特点：

```
相对来说不太安全，因为密码不应该显示在地址栏。
不能传递海量数据，因此地址长度有限制。url字符最大长度65535
最大不能超过4kb chrome8k
不能上传附件。
```

注意：`只要是通过地址栏，向服务器传数据的，一定是GET传递方式。`

POST的特点：

```
相对来说比较安全。包传递
可以传递海量数据，长度没有限制。
可以上传附件。
```

注意：`POST方式只能用在表单中，其它地方不会用来。`

```html
<form name="form"  method="post" action="">
	<table >
		<tr>
			<td>用户名:
            </td>
			<td><input type="text" name="username" value="" placeholder='请输入账号'/>
            </td>
		</tr>
		<tr>
			<td >密码:
            </td>
			<td><input type="password" name="password" value="" placeholder='请输入密码'/>	
            </td>
		</tr>
	</table>
</form>
```

####表单元素：单行文本框

```html
<input type = “text” 属性 = “属性值” />
常用属性：
type：元素的类型。取值：text、password、radio、checkbox、button、submit、reset等。
name：表单元素的名称。可以包含a-z、A-Z、0-9、_这些符号，但不能以数字开头。
value：元素的值。
size：文本框的长度，以字符为单位。
maxlength：最多可以输入的字符数
readonly：只读属性。如：readonly = “readonly”
disabled：禁用属性。如：disabled = “disabled”
```

注意：`单行文本框是有长度限制的，最多只能输入255个字节`。

####单行密码框

```html
<input type = “password” 属性 = “属性值”  />
常用属性：
type：元素的类型。
name：元素的名称
value：元素的值
size：密码框的长度，以字符为单位
maxlength：最多可以输入的字符数
readonly：只读属性。如：readonly = “readonly”
disabled：禁用属性。如：disabled = “disabled”
```

####单选框

```html
<input  type = “radio” 属性 = “属性值” />
常用属性:
type：元素类型
name：元素名称
value：元素的值
checked：是否默认选中。checked=“checked”
```

注意：`单选按钮是一组相互排斥的，名称应该一样，但提交的值只能是其中一个`。

#### 复选框

```html
<input  type = “checkbox” 属性 = “属性值” />
常用属性:
type：元素类型
name：元素名称
value：元素的值
checked：是否默认选中。checked=“checked”
```

注意：复选框也是一组选项，名称必须一致。可以全选，也可以都不选。定义的时候name最好是个数组。

####下拉列表

```html
<select name="dot">
	<option value="">..请选择</option>
	<option value="1">巴厘岛</option>
	……
</select>
select属性：
name：元素的名称。
option属性：
value：元素的值
selected：是否默认选中。 	selected=“selected”
```

####文本区域

```html
<textarea 属性 = “属性值”>默认文本</textarea>
常用属性：
name：元素名称
value：元素的值，不能直接给<textarea>元素添加value属性。
cols：宽度，是多少个字符宽。
rows：高度，是多少个字符高度。
```

#### 隐藏域

```html
<input  type = “hidden”  name = ""  value = ""  />
```

隐藏标签，不显示在网页中，也不显示在源代码中。目的是为了防止CSRF攻击

#### 上传文件域

```html
<input  type = “file”  属性 = “属性值”  />
常用属性:
name：元素的名称。
value：元素的值，应该是上传的文件名称。
```

注意：基于安全方面的考滤，value属性是只读属性。

#### 表单中的5种按钮

```html
<input  type = “submit”  value = “提交表单”  />
<input  type = “reset”  value = “重新填写”  />
<input type="image" src="images/btn02.png" />
<input type='button' name='button' value='按钮' />
<button>
    也是按钮,
</button>
```







##颜色表示

用颜色单词表示：red、green、blue、white、black  rainbow
用10进制表示：rgb(255,0,0) 、rgb(0,255,0)、rgb(0,0,255)、rgb(255,255,255)、rgb(0,0,0)
用16进制表示：#FF0000、#00FF00、#0000FF



详情：aug8/aug12,aug8/aug13。开始学习html周一周二



