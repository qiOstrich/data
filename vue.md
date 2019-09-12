# vue学习

```javascript
//实例化vue对象
var a_vue = new Vue({
    el:"#idm", //绑定id为idm的块标签
    data:{data1:"",data2:"",……},   //存放变量
    methods:{
	func1(),
	func2(),
    func3(),
    ……
    }, //存放函数
});
v-on:click = "func1()"; //标签属性：绑定函数
@click= "func2()";//也是绑定函数语句
v-bind:value = "data1" ;//单向绑定value属性
v-model:value = 'data2';//双向绑定value属性
v-text="data3";//插值表达式，替换内容
v-cloak;  //解决闪动问题
//闪动问题是插值表达式因网络慢而暂时没有替换，随加载的进行缓慢替换，显示这一现象的过程叫闪动

```



## 插值表达式

```javascript
//双行标签插入内容的表达式
<>{{data1}}<>
//这里的data1就会被vue里data中的变量代替。
v-text='data1';//也能改变内容
```

## 事件修饰符

```javascript
//事件冒泡：多标签的叠加，在触发最上层标签事件的同事也触发了其下层标签的事件。
//事件修饰符： 
stop //停止时间冒泡
self //不参加事件冒泡
once //事件只触发一次，之后解绑
capture //事件捕获，先添加的先出发。从外到内触发
prevent //阻止默认行为

//用法：
v-on:click.事件修饰符
```

## 类样式控制

```html
控制class：
在css中定义类样式:
<style>
    .class1{……}
    .class2{……}
    .class3{……}
    .class4{……}
    ……
</style>
:class='["class1","class2",……]'
:class='[{"class1":flag,"class2":flag,……}]'
flag是一个bool变量
```

## css样式控制

```
//在vue对象中定义data属性
data:{
style1:{"color":'purple',"letter-spcing":'1em'},
style2:{"font-size":"20px"},
style3:{
	one:{"color":'purple',"letter-spcing":'1em'},
	two:{"font-size":"20px"},
	……
},
//标签中添加属性:
:style="{style1,……}"
:sryle="[style3.one,……]"
```

##vue中的循环

```
在vue使用ajax存在不兼容问题。需要追加引入vue-resource文件
在定义jquery不适用$.ajax({}),
使用this.http.get(url,params).then(func);
url中给路径参数，params可以省略，暂时用不到，
then()表示请求成功，得到数据:
then(function(msg){
	msg表示的请求得到的返回数据
});

<tr v-for="(item,i) in arr" :key="item.id">
	<td><input type="checkbox" v-bind:value="item.id"></td>
	<!-- v-for: key属性，被key绑定的值是唯一的，重复会报错 -->
	<td v-for="(valu,keys) in item" v-text="valu"></td>
	<td><a href="#" @click="del(item.id)">删除</a></td>
</tr>
arr是script中的数值。

```

详情：aug8/aug22中aug22_learn_vue5文件

















