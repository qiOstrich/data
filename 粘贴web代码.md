# marquee跑马灯

```html
<marquee direction='left' width='400px' height='300px' bgcolor='#ffff66' scrollAmount='100' scrollDelay='40'>
<p>我是漂浮物</p>
</marquee>
```

# img图片

```html
<img src="路径"/ alt="加载失败提示字">
```



# 锚点的应用

```html
<a name='top'></a> 
<a href='#top'>点我回到top锚点</a>
```

# meta关键字

```html
<meta name="keywords" content="爬虫所找的关键字" />
<meta name="description" content="搜索关键字描述"/>
```

# meta实现移动端网页

```html
<meta name="viewport" content="width=device-width,minimum-scale=1.0,maximum-scale=1.0,maximum-scale=1.0,user-scalable=0"/>
```

# audio音频

```html
<audio src="images_2/horse.ogg" controls="controls">
Your browser does not support the audio element.
</audio>
```

# video视频

```html
<video src="images_2/movie.ogg" controls="controls">
your browser does not support the video tag
</video>
```

# flash动画embed

```html
<embed src="images_2/banner.swf" width="100%"  quality="high" pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash" wmode="transparent"></embed>
```

进程做运算，线程做io读写很快。协程yeild 在网络io的时候，

#css开头必写

```html
*{margin:0px;padding:0px;}
ul,li,ol{list-style:none;}
img{border:0;}
*{font-size:0;} 可以写，但是么得必要。
```

# jquery事件

blur(fn)：失去焦点时触发 (输入完成时触发)**<u><-matter</u>   **

change(fn)：状态改变时触发 (输入框内容改变)**<u><-matter</u>   **
click(fn)：点击时触发**<u><-matter</u>   **
dblclick(fn)：双击时触发
focus(fn)：获得焦点时触发
keydown(fn)：键盘按下时触发
keyup(fn)：键盘弹起时触发
keypress(fn)：键盘按起时触发**<u><-matter</u>   **
load(fn)：页面载入时触发，功能与ready类似
unload(fn)：页面关闭时触发
mousedown(fn)：鼠标按下时触发**<u><-matter</u>   **
mouseup(fn)：鼠标弹起时触发
mousemove(fn)：鼠标移动时触发
mouseover(fn)：鼠标悬浮时触发**<u><-matter</u>   **
mouseout(fn)：鼠标离开时触发**<u><-matter</u>   **
resize(fn)：调整大小时触发
scroll(fn)：滚动时触发**<u><-matter</u>   **
select(fn)：文本选中时触发
submit(fn)：表单提交时触发





