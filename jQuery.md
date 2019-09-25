# @jQuery

封装过的js框架，体积小，简化了对HTML、CSS、DOM、事件、动画的处理。

##各种选择器

```html
<script src='name.js'></script>//不能加内容
<script>
$(function(){
    $("#idname");//匹配id是idname的标签
    $(".classname");//匹配class是classname的标签
    $("p");//匹配p标签
    $("p,li,……");//匹配多个标签
    $("div p");//匹配所有后代元素（多级后代）
    $("div>p");//匹配子元素（一级子）
    $("div+ul");//匹配同级元素的下一个元素
    $("span~span");//匹配所有同级元素
    $("ul>:first");//匹配ul子元素的第一元素
    $("ul>:last");//匹配ul子元素的尾元素
    $("ul>:even");//匹配偶数
    $("ul>:odd");//匹配奇数
    $("ul>:gt(3)");//匹配索引大于3（n）的元素
    $("ul>:lt(3)");//匹配索引小于3（n）的元素
    $("ul>:eq(3)");//匹配索引等于3（n）的元素
    $("ul>:not(object)");//匹配索引不是object的元素，括号内可以是其他匹配式
    $("ul>:contains(内容)");//匹配包含指定文本的元素
    $('ul>:empty');//匹配ul子类中的空元素
    $('ul>:has(tag)');//匹配含有tag标签的元素
    $("ul>:parent");//匹配作为父元素(含有非空子元素)的元素
    $("body>:hidden");//匹配不可见元素
    $("body>:visible");//匹配可视元素
    $("[value]");//匹配含有value属性的元素
    $("[value=value]");//匹配value属性是value的元素
    $("body>[name!=notname]");//匹配name属性不是notname的元素
    $("[id^=id]");//匹配id属性的值以id开始的元素
    $("[id$=id]");//匹配id属性的值以id结束的元素
    $("[id*=id]");//匹配id属性的值含有id的元素
    $("[id][name][……]");//匹配含有id，name，……等属性的元素
    $(":input");//匹配input标签
	$(":submit");//匹配type是submit的元素
	$(":password");//匹配type是password的元素
	$(":reset");//匹配type是reset的元素
	$(":radio");//匹配type是radio的元素
	$(":text");//匹配type是的text元素
	$(":checkbox");//匹配type是chenkbox的元素
	$(":hidden");//匹配type是hidden的元素
	$(":image");//匹配type是image的元素
	$(":button");//匹配type是button的元素
	$(":file");//匹配type是file的元素
	$(":enabled");//匹配所有可用的元素
	$(":checked");//匹配复选框选择的元素
	$(":disabled");//匹配所有不可用的元素
	$(":selected");//匹配下拉选框选择的元素
    :only-child//匹配只有一个子元素的元素
    :last-child//匹配最后一个子元素
    :first-child//匹配第一个子元素
    :nth-child(index/even/odd) //从1算起匹配索引为index的指定元素
</script>
```

## jQuery属性

### attr属性

```html
attr(name)//获取对象属性的值
attr(key,value)//改变属性的值
attr({id:"id",name:"name",……})//同时改变多个属性的值
attr(key,function)//通过函数，进行判断，通过返回值改变属性的值
removeAttr(name)//移除属性的值
```



### class属性

```html
addClass(class)//为元素添加class属性
removeClass(class)//移除元素的class属性
toggleClass(class)//切换样式，没有
hasClass(class)//判断是否有class属性
```



### css属性

```html
css(name)//取得元素样式的属性
css(name,value)//改变元素样式
css({width:"20px",height:"40px",……})//同时为元素设置多个样式属性
```

详情：aug8/aug19 学习**选择器**到**css属性**。aug19，周一。



### 常用的事件

```javascript
blur(fn);//文本失去焦距触发事件 matter
change(fn);//文本状态改变触发事件
click(fn);//单击事件 matter
dblclick(fn);//双击事件matter
focus(fn);//获得焦点触发事件（文本）matter
keydown(fn);//按下键帽触发$(document).keydown(function(e){
//console.log(e.keyCode);})matter

keyup(fn);//松开键帽触发
keypress(fn);//键入时触发
load(fn);//加载时触发
unload(fn);//网页关闭触发
mousedown(fn);//鼠标按下触发
mouseup(fn);//鼠标松开触发
mousemove(fn);//鼠标移动触发matter
mouseover(fn);//鼠标指向其时触发matter
mouseout(fn);//鼠标离开指向触发matter
resize(fn);//调整大小触发
scroll(fn);//滚动使触发
select(fn);//文本选中时触发
submit(fn);//表单提交按钮触发

hover(overfunc,outfunc);//鼠标悬浮和离开时触发的不同事件matter

```



### 绑定事件bind

除了上一个标题能够直接绑定事件以外，还有别的语句进行绑定语句。

```javascript
bind("eventname",[args],func(args){});//bind与on用法相同；把事件名和函数绑定在一起使用{"eventname":func,……}可以实现多个绑定
one("eventname",[args],func(args){});//同是绑定，但是只执行一次
unbind(['eventname,……']);//解除事件名的绑定

```

### this自己的用法

this表示对象自己。与python中self相似

IE5、6指向window对象

W3C指向当前操作对象



### 基本动画

```javascript
show();//显示jquery对象
hied();//隐藏jquery对象
//可添加参数：speed速度,[callback]动画完成时回调函数

slideDown();//动画效果向下滑动显示
slideUp();//动画效果向上滑动隐藏
slideToggle();//动画效果切换显示/隐藏
//可添加参数：speed速度,[callback]动画完成时回调函数

fadeIn();//动画效果淡入
fadeOut();//动画效果淡出
fadeToggle();//切换淡入/淡出
//可添加参数：speed速度,[callback]动画完成时回调函数
fadeTo(speed,opacity,[callback]);//opacity：0~1透明度

```



### 文档操作

```javascript
A.append(B);//在A标签内的结尾添加B（B可以是标签字符或者是jquery对象）
B.appendTo(A);//把B添加到A标签内的结尾处

A.prepend(B);//A内开头添加B
B.prependTo(A);//把B加载A内的开头

A.after(B);// B加在A标签的后面
B.insertAfter(A);//把B插到A的前面

A.before(B);//B加在A标签的后面
B.insertBefore(A);//把B插到A的前面


```



###删除操作

```javascript
empty();//清空元素内容
remove();//删除元素，节点，内容
```



### 复制操作

```javascript
clone();//复制元素，可以clone（onclick），onclick是属性。
clone(true);//复制元素，包括元素的事件
```



###替换操作

```javascript
html();//值替换，添加字符
replaceWith();//标签替换，添加jquery对象
```



### 包裹操作

```javascript
wrap();//使用参数标签包裹原标签
wrapAll();//
wrapInner();//
```





### 查找操作

```javascript
eq(index);//通过元素的索引查找元素
filter(callback);(过滤)//查找与参数匹配的元素
//callback可以是一个有返回值的函数
not(part);//查找与参数不匹配的元素
find(part);//查找所有后代元素，若无参数找所有匹配的元素
next([part]);//查找紧邻的下一个元素
nextAll();//查找之后的所有的元素
nextUntil(tag);//查找之后的元素，直到找到tag
prev([part]);//查找上一个元素
prevAll([part]);//查找紧邻的上一个与之前所有的元素
prevUntil(tag);//查找之前的元素，直到找到tag
parent([part]);//查找当前元素的父元素
children([part]);//查找所有子元素
siblings([part]);//查找所有同级的元素
```

详情：aug8/aug20文件s夹，学习**常用事件**到**查找操作** aug20,周二。



### each（）

与filter（）用法一致。

```javascript
$(msg).each(function(i,item){

//i是下标或索引，item是索引对应的数据,xml和json返回object

})
//msg表示success得到的数据

```





### ajax



Asynchronous 异步

Javascript js

And 和

XML xml文件

可以在页面不刷新的情况下，完成bs交互

```javascript
$.ajax({
    url:"http://localhost.qmx.com:8080", //路径，链接
    type:"get",//请求方式 get post putpatch delete
    data:'text',//发送的数据，可以是text，json
    dataType:"text",//返回数据格式，text，json，xml
    success:function(msg){
        //msg是求情成功后得到的返回数据
    },
});
```

详情：immy文件夹。学习ajax，each（）。aug21，周三。























