# css学习

## 语法格式

```html
<style type="text/css">
	h1 {color:red;font-size:12px;}
</style>
```

css选择器方式：

1. 嵌入式
2. 外链式
3. 行内式

## css选择器的优先级

（1）单个选择器优先级

行内样式 > Id选择器 > 类选择器 > 标签选择器

##css选择器类型

1. 类选择器，可以实现多个类调用，中间加空格 

```html
.name{属性}  声明
< class="name" > 调用
```

2. id选择器，只能实现一个id调用，少用

```html
#id{属性} 声明
< id="id" > 调用
```

3. 标签选择器，通过声明标签直接改变所有标签，自动调用，多个使用逗号隔开，*代表所有标签。

```html
p,li,ol{属性}
*{属性}
```

4. 子类选择器，某种选择器的子类标签

```html
#id>p {属性}
选择指定id的子类p，只选择子类这一级中的p
```

5. 后代选择器，与子类选择器类似，但是不止一级

```html
.name p{属性}
选择指定类中的所有p，只要在其标签中的p都会被选择
```

6. 伪类选择器

- :link  正常链接效果。
- :visited   访问过的效果
- :hover  鼠标放上的效果
- :active   激活状态(鼠标点击的一瞬间出现一般不用)
- `这4个的顺序一定不能弄错,弄错了就没有效果`

## 属性

### px，em，rem

px为像素，固定值

em为相对长度，相对父类的长度属性，父类没有长度则相对浏览器的默认尺寸，一般为16px；

rem也是相对长度，只想对于浏览器的默认长度：16px

### 尺寸属性:px/em/rem

+ width 宽度，单位px、em、rem
+ height 高度

### 字体属性:font

- font-size : 文字大小
- font-weight : 加粗效果，值：bold
- font-style : 斜体效果，值：italic
- font-family : 字体类型，如楷体

### 文本属性:text

- color : 文本颜色，red / #ffffff /rag(r,g,b)
- line-height : 行高，可以是百分比，也可以是固定px
- text-align : 对齐方式，left，center，right
- letter-spacing : 字间距。
- text-decoration : 文本修饰线，值none,underline,overline,line-through
- text-indent :首行缩进，值为px。

### 列表属性:list-style

- list-style : 值none，取出有序列表序号，无序列表点

### 边框属性:border

- border- left : 左边框线，
- border-right : 右边框线
- border-top : 顶边框线
- border-bottom : 下边框线
- border : 四周线，格式：px linetype color；px是固定像素，linetype是线的形式：none / solid实线 / dotted点状线 / dashed虚线/  double双线
- borer-collapse : collapse，合并表格边框线。

### 填充属性:padding,margin

- padding-left : 左内填充距离
- padding-right : 右内填充距离
- padding-top : 上内填充距离
- pading-bottom : 下内填充距离
- padding : px; 四边内填充距离
- padding : px px;上下，左右，
- padding : px px px;上，左右，下
- padding : px px px px; 上，右，下，左

margin用法与padding相同

margin是外边距，padding是内边距

###背景属性:background

- background-color : 背景颜色
- background-image :  背景图片，路径或链接，url（路径）
- background-repeat : 背景图片平铺方式，值：no-repeat不平铺、repeat-x水平平铺、repeat-y垂直平铺、repeat四周平铺
- background-position: 图片位置，三种定位方式：
  - 单词定位：left、center、right、top、bottom
  - 百分比定位。
  - 像素定位，冒号后直接跟像素。

简写方式:
	`格式：background：背景色 图片的路径 平铺方式 定位方式`

example：

```html
background:white url(images/02.gif) no-repeat 480px bottom;
```

### 浮动属性和清除:float

浮动：

- float : 浮动，值left，right
- CSS浮动可以使元素向左或向右浮动。浮动到父元素的边上或者上一个浮动元素的边上。
- 浮动的元素不再占空间了。
- 浮动的元素层级高于普通元素(没有浮动)。
- 浮动的元素一定是块元素，不管以前是什么元素。换句话：行内元素浮动以后，也变成了块元素。

清除浮动：

- clear：清除浮动，取值：left、right、both(两者)`clear:both;`
- 一般情况下，上面有浮动，下面就得清除浮动
- 先浮动，后清除；有浮动，必须要有清除浮动
- 清除浮动后，可以让父元素在“视觉”上包含浮动元素
- 清除浮动后，清除浮动之后的其它元素，将恢复默认排版(不再继承上面的浮动特性)

###显示方式:display

display有三个值，none，block块显示，inline行显示。用于改变显示方式。可以改变元素排版。

注意：元素隐藏不再占空间了。

### 文字溢出处理:overflow

overflow有四个值：viisble（可见，默认值）、scroll（滚动）、hidden（隐藏）、auto（自动，一般的选择）。

###光标显示类型:cursor

cursor的值有4个：pointer（小手）、help（帮助）、text（文本）、wait（等待）。

光标指向某个元素变换类型，一般默认就行。

### 定位属性:position

position有4个值：static：静态，默认值；

fixed：固定位置，广告，页面菜单栏等；

relative：相对定位，相对父级标签的定位；

absolute：绝对定位，默认相对浏览器边框，父级给定了位置则相对父级的绝对位置，配合<b>lrtb</b>使用；

position值的坐标值。

<b>l</b>eft：距离目标元素左边的距离。

<b>r</b>ight：距离目标元素右边的距离。

<b>t</b>op：距离目标元素顶边的距离

<b>b</b>ottom：距离目标元素底边的距离。
提示：如果不指定定位坐标值，定位元素在“原地不动”。

## 盒子模型

标签可以看做盒子，有内外间距（margin，padding）。



详情：aug8/aug13,aug8/aug14 。 13下午学习css。

周二，周三。

