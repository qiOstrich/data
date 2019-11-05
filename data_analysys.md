# 数据学习

# ！！！以下代码皆在jupyter notebook中运行

## 1 Jupyter Notebook 的快捷键

Jupyter Notebook 有两种键盘输入模式。编辑模式，允许你往单元中键入代码或文本；这时的单元框线是绿色的。命令模式，键盘输入运行程序命令；这时的单元框线是灰色。

### 1.1 命令模式 (按键 Esc 开启)

- **Enter** : 转入编辑模式
- **Shift-Enter** : 运行本单元，选中下个单元
- **Ctrl-Enter** : 运行本单元
- **Alt-Enter** : 运行本单元，在其下插入新单元
- **Y** : 单元转入代码状态
- **M** :单元转入markdown状态
- **R** : 单元转入raw状态
- **1** : 设定 1 级标题
- **2** : 设定 2 级标题
- **3** : 设定 3 级标题
- **4** : 设定 4 级标题
- **5** : 设定 5 级标题
- **6** : 设定 6 级标题
- **Up** : 选中上方单元
- **K** : 选中上方单元
- **Down** : 选中下方单元
- **J** : 选中下方单元
- **Shift-K** : 扩大选中上方单元
- **Shift-J** : 扩大选中下方单元
- **A** : 在上方插入新单元
- **B** : 在下方插入新单元
- **X** : 剪切选中的单元
- **C** : 复制选中的单元
- **Shift-V** : 粘贴到上方单元
- **V** : 粘贴到下方单元
- **Z** : 恢复删除的最后一个单元
- **D,D** : 删除选中的单元
- **Shift-M** : 合并选中的单元
- **Ctrl-S** : 文件存盘
- **S** : 文件存盘
- **L** : 转换行号
- **O** : 转换输出
- **Shift-O** : 转换输出滚动
- **Esc** : 关闭页面
- **Q** : 关闭页面
- **H** : 显示快捷键帮助
- **I,I** : 中断Notebook内核
- **0,0** : 重启Notebook内核
- **Shift** : 忽略
- **Shift-Space** : 向上滚动
- **Space** : 向下滚动

### 1.2 编辑模式 ( Enter 键启动)

- **Tab** : 代码补全或缩进
- **Shift-Tab** : 提示
- **Ctrl-]** : 缩进
- **Ctrl-[** : 解除缩进
- **Ctrl-A** : 全选
- **Ctrl-Z** : 复原
- **Ctrl-Shift-Z** : 再做
- **Ctrl-Y** : 再做
- **Ctrl-Home** : 跳到单元开头
- **Ctrl-Up** : 跳到单元开头
- **Ctrl-End** : 跳到单元末尾
- **Ctrl-Down** : 跳到单元末尾
- **Ctrl-Left** : 跳到左边一个字首
- **Ctrl-Right** : 跳到右边一个字首
- **Ctrl-Backspace** : 删除前面一个字
- **Ctrl-Delete** : 删除后面一个字
- **Esc** : 进入命令模式
- **Ctrl-M** : 进入命令模式
- **Shift-Enter** : 运行本单元，选中下一单元
- **Ctrl-Enter** : 运行本单元
- **Alt-Enter** : 运行本单元，在下面插入一单元
- **Ctrl-Shift--** : 分割单元
- **Ctrl-Shift-Subtract** : 分割单元
- **Ctrl-S** : 文件存盘
- **Shift** : 忽略
- **Up** : 光标上移或转入上一单元
- **Down** :光标下移或转入下一单元



### jupyter notebook命令

 简单的魔法指令

 `%run` 运行外部的python文件

 `%whos` 查看声明了那些变量和函数



### numpy

-> numeric python 数字化的python  

 numpy 中最重要的一个形式叫 `ndarray` 

n 表示的是n个 d dimension 维度 array 数组 

标量 : 0维；

向量 : 1维；

矩阵 : 2维；

张量 : 3维及多维；

\#matplotlib 图形展示库

\#pandas 数据分析库



```
Python 本身支持的数值类型有 int（整型，python2 中存在 long 长整型）、float（浮点型）、bool（布尔型） 和 complex（复数型）。

而 Numpy 支持比 Python 本身更为丰富的数值类型，细分如下：

bool：布尔类型，1 个字节，值为 True 或 False。

int：整数类型，通常为 int64 或 int32 。

intc：与 C 里的 int 相同，通常为 int32 或 int64。

intp：用于索引，通常为 int32 或 int64。

int8：字节（从 -128 到 127） tinyint

（tinyint 1字节 -2 ^7 ~ 2^7-1 (-128~127)）

int16：整数（从 -32768 到 32767） smallint

(smallint 2字节 -2 ^15 ~ 2^15-1 (-32768~32765))

int32：整数（从 -2147483648 到 2147483647） int

（int 4字节 -2 ^31~ 2^31-1 (-2147483648~2147483647)）

int64：整数（从 -9223372036854775808 到 9223372036854775807） bigint

（bigint 8字节 -2 ^63 ~ 2^63-1）

uint8：无符号整数（从 0 到 255） unsigned

uint16：无符号整数（从 0 到 65535）

uint32：无符号整数（从 0 到 4294967295）

uint64：无符号整数（从 0 到 18446744073709551615）

float：float64 的简写。

float16：半精度浮点，5 位指数，10 位尾数

float32：单精度浮点，8 位指数，23 位尾数

float64：双精度浮点，11 位指数，52 位尾数

complex：complex128 的简写。

complex64：复数，由两个 32 位浮点表示。

complex128：复数，由两个 64 位浮点表示。

20.pandas.datetimes 时间类型

在 Numpy 中，上面提到的这些数值类型都被归于 dtype（data-type） 对象的实例。

我们可以用 numpy.dtype(object, align, copy) 来指定数值类型。而在数组里面，可以用 dtype= 参数。
```



### ndarray详解

```
Numpy 中，ndarray 类具有六个参数，它们分别为：
>>shape：数组的形状。

>>dtype：数据类型。

buffer：对象暴露缓冲区接口。

offset：数组数据的偏移量。

strides：数据步长。

order：{'C'，'F'}，以行或列为主排列顺序
```

 下面，我们来了解创建 ndarray 的一些方法。在 numpy 中，我们主要通过以下 5 种途径创建数组，它们分别是： 

##### 1.从 Python 数组结构列表，元组等转换。

##### 2.使用 np.arange、np.ones、np.zeros 等 numpy 原生方法。

##### 3.从存储空间读取数组。

##### 4.通过使用字符串或缓冲区从原始字节创建数组。

##### 5.使用特殊函数，如 random。

```
numpy.array 将列表或元组转换为 ndarray 数组。其方法为：
numpy.array(object, dtype=None, copy=True, order=None, subok=False, ndmin=0) 
其中，参数：
object：列表、元组等。
dtype：数据类型。如果未给出，则类型为被保存对象所需的最小类型。
copy：布尔来写，默认 True，表示复制对象。
```



```
除了直接使用 array 方法创建 ndarray，在 numpy 中还有一些方法可以创建一些有规律性的多维数。首先，我们来看一看 arange()。
arange() 的功能是在给定区间内创建一系列均匀间隔的值。方法如下：

numpy.arange(start, stop, step, dtype=None)  
你需要先设置值所在的区间，这里为 ``[开始， 停止）`，你应该能发现这是一个半开半闭区间。然后，在设置`step`步长用于设置值之间的间隔。最后的可选参数`dtype`可以设置返回`ndarray` 的值类型。
```



```
linspace方法也可以像arange方法很像，创建数值有规律的数组。inspace用于在指定的区间内返回间隔均匀的值。其方法如下：

numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None) 
start：序列的起始值。
stop：序列的结束值。
num：生成的样本数。默认值为50。
endpoint：布尔值，如果为真，则最后一个样本包含在序列内。
retstep：布尔值，如果为真，返回间距。
dtype：数组的类型。

logspace是类似linspace的方法，线性生成

```



```
ones 方法创建
numpy.ones 用于快速创建数值全部为 1 的多维数组。其方法如下：

numpy.ones(shape, dtype=None, order='C')
其中：
shape：用于指定数组形状，例如（1， 2）或 3。
dtype：数据类型。
order：{'C'，'F'}，按行或列方式储存数组。
```



```
zeros 方法创建

zeros 方法和上面的 ones 方法非常相似，不同的地方在于，这里全部填充为 0。zeros 方法和 ones 是一致的。
numpy.zeros(shape, dtype=None, order='C')
其中：
shape：用于指定数组形状，例如`（1， 2）`或`3`。
dtype：数据类型。
order：{'C'，'F'}，按行或列方式储存数组。
```



```
逆矩阵
逆矩阵矩阵的倒数,必须是方阵,满秩矩阵->奇异矩阵
np.linalg.inv(array_obj)
```



```
np.diag构建对角矩阵 np.diag(v,k=0)参数为列表即可

v可以是一维或二维的矩阵
k<0表示斜线在矩阵的下方
k>0表示斜线在矩阵的上方
```

##### 

```
full方法创建
numpy.full用于创建一个自定义形状的数组，可以自己指定一个值，该值填满整个矩阵。
numpy.full(shape,fill_value=num)
也有dtype，shape，order等参数
```



```
eye 方法创建

numpy.eye 用于创建一个二维数组，其特点是k 对角线上的值为 1，其余值全部为0。方法如下：
numpy.eye(N, M=None, k=0, dtype=<type 'float'>) 
#k表示从下标第几个开始
其中：
N：输出数组的行数。
M：输出数组的列数。
k：对角线索引：0（默认）是指主对角线，正值是指上对角线，负值是指下对角线。
```

##### 

```
生成随机的整数型矩阵
np.random.randint(low=0,high=150,size=(5,4))
low 表示的是最小值
high 表示最大值
size 是一个元组类型,=shape

随机抽样
np.random.random(size=(456,730,3))
size 表示形状 random随即生产的范围是0-1之间
```



```
正态分布
np.random.randn(10,5)
没有固定的参数，每多加一个数字，代表多增加一个维度

np.random.normal(loc=170,scale=100,size=50)
normal也是一个正太分布的方法

生成一个一维数组

location 是定位的的值
scale 是波动值
size 是数据长度
```



```
随机数
每一个数据，都是一个维度

rand 和 random 的区别：random 需要 size来描述形状，而rand只需要我们直接给值,通过值的数量来确定形状

np.random.rand(d1,d2,dn)
```



```python
CSV
csv,dat是一种常用的数据格式化文件类型，为了从中读取数据，我们使用
import matplotlib.pyplot as plt
jj = plt.imread('jingjing.png')
np.savetxt('jj.csv',jj[0],delimiter=';')
np.loadtxt('jj.csv',delimiter=';')
```



```
Numpy 原生文件类型
使用 numpy.save 与 numpy.load 保存和读取：
np.save('jj.npy',jj)
np.load('jj.npy')
```



###### 例子

```python
import numpy as np

# 定义一个3行4列的数组，内容随机，并且是一字节整数
a = np.ndarray(shape(3,4),dtype=np.int8)

list_1 = [[1,2,3],[1,2,3],[1,2,3],[1,2,3],[1,2,3]]

#使用array进行强制类型转换，可以转列表和元组
qzzh = np.array(list_1)
#可以使用下标得到具体数据
qzzh[0,0] # 得到第一行第一列的数据 这里是 1

display(qzzh) # 原样输出这个序列

# 等差数列
b = np.arange(5,10,2) # 得到5到9的序列,间隔为2

# linspace
c = np.linspace(start=0,stop=10,num=100)
# 得到100个在0到10之间的随机数


# logspace
d = np.logspace(start=1,stop=10,num=10)
# 默认以10为底，生成
# 补充
np.log(np.e) # 1 log函数默认以e为底

# ones
e = np.ones(shape=(4,5)) #生成一个4行5列值全部为1的矩阵

# full
f = np.full(shape(3,3),fill_value=np.e,)
# 使用e填充矩阵


# eye
g = np.eye(3)
# 生成一个3行3列且主对角线是1的矩阵

# 逆矩阵
h = np.array(array_obj)
# 求array_obj的逆矩阵

# 随机生成整型
i = np.random.randint(0,256,size=(5,3),dtype=np.uint8)

#正态分布
j = np.random.randn(5,3)

# 随机抽样
k = np.random.random(size=10)

# 生成一个正态分布的数组（序列）
l = np.random.normal(loc=170,scale=10,size=10)

#也是随机数，不同在参数
o = np.random.rand(5,3)

# 补充
np.dot(array1,array2)
# 矩阵相乘，需要符合矩阵乘法原理，不然报错
array_obj.mean() # 求平均值
array_obk.std() # 求标准差
array_obk.var() # 求方差


import matplotlib.pyplot as plt

#可以使用matplotlib.pyplot读取图片
cat = plt.imread('./cat.jpg')  # 得到三维数组，其中第三列为RGB颜色属性

plt.imshow(cat) #可以将读取到的图片进行展示，并附有坐标
```



###### 读取图片的函数

`pyplot.imread()`

返回一个numpy.ndarray，图形转换成为的数组

###### 展示图片的函数

pyplot.imshow()

无返回值





#### ndarray 数组属性

```
ndim,shape,size¶
ndim 数组的维度 （自己会计算）
shape 形状（5,4，3）
size 数组的总长度
dtype 查看数据类型
```

例子：

```python
array_obj = [[1,2,3],[1,2,3],[1,2,3],[1,2,3]]
array_obj.ndim  
array_obj.shape 
array_obj.size
array_obj.dtype
```



#### 在定义的时候可以通过dtype来定义数据的类型

使用 ndarray.astype() 方法进行转换

例子：

```python
new_jj = plt.imread('./jingjing.png')
new_jj = (jj*255).astype(np.uint8)
plt.imsave('jj.jpg',new_jj)
plt.imshow(new_jj)
```

#### ndarray.T

`ndarray.T`用于数组的转置，与 `.transpose()` 相同。

```
plt.imshow(new_jj[:,:,::-1])
```



#### ndarray.imag

ndarray.imag  用来输出数组包含元素的虚部。

imaginary number 虚数

```
com=np.full((5,3),fill_value=1.234+0.11j)
com.imag #只取复数的虚部
```



#### ndarray.real

`ndarray.real`用来输出数组包含元素的实部。

```
com.real # 取实部
```



####  ndarray.itemsize

`ndarray.itemsize`输出一个数组元素的字节数

```
one = np.ones(shape=(4,5),dtype=np.int8)
one.itemsize
```



#### ndarray.nbytes

`ndarray.nbytes`用来输出数组的元素总字节数。



```
one = np.ones(shape=(4,5),dtype=np.int8)
one.nbytes
```



#### ndarray.strides
`ndarray.strides`用来遍历数组时，输出每个维度中步进的字节元组。

```
one = np.ones(shape=(4,5),dtype=np.int8)
one.strides
```















