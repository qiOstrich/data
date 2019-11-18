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

###### ndarray.T

`ndarray.T`用于数组的转置，与 `.transpose()` 相同。

```
plt.imshow(new_jj[:,:,::-1])
```



###### ndarray.imag

ndarray.imag  用来输出数组包含元素的虚部。

imaginary number 虚数

```
com=np.full((5,3),fill_value=1.234+0.11j)
com.imag #只取复数的虚部
```



###### ndarray.real

`ndarray.real`用来输出数组包含元素的实部。

```
com.real # 取实部
```



######  ndarray.itemsize

`ndarray.itemsize`输出一个数组元素的字节数

```
one = np.ones(shape=(4,5),dtype=np.int8)
one.itemsize
```



###### ndarray.nbytes

`ndarray.nbytes`用来输出数组的元素总字节数。



```
one = np.ones(shape=(4,5),dtype=np.int8)
one.nbytes
```



###### ndarray.strides
`ndarray.strides`用来遍历数组时，输出每个维度中步进的字节元组。

```
one = np.ones(shape=(4,5),dtype=np.int8)
one.strides
```



### Numpy数组的基本操作

#### 索引(下标)

与列表基本一致，但是多一种方式

```
array_obj[0,2,3]
# 取数组中的第一个数组中的第3个数组中的第4个数组
# 与列表下标list_obj[0][2][3]操作一样，并且可以这么写
```

#### 重设形状

reshape 可以重设形状，但是总量不能改变，即此处减少多少，就要在别处加上多少。

reshape 可以在不改变数组数据的同时，改变数组的形状。其中，numpy.reshape() 等效于 ndarray.reshape()。

```
#在改变形状的过程中，元素的总量是不能发生改变的
#cmap：color  map遍历
#-1代表的是剩余的元素 483×3
plt.imshow(lj.reshape(483,-1),cmap='gray')
```



#### 数组展开

降维，降到一维

```
array_obj.ravel()
```



#### 级联

1. np.concatenate() 级联需要注意的点：
2. 级联的参数是列表：一定要加中括号或小括号
3. 维度必须相同
4. 形状相符
5. 【重点】级联的方向默认是shape这个tuple的第一个值所代表的维度方向
6. 可通过axis参数改变级联的方向，默认为0, （0表示列相连,行发生改变,表示的Y轴的事情，1表示列相连,列发生改变,X轴的事情）

```
rh = plt.imread('ruhua.jpg')
nz = rh[:,0:483]
xg = lj[:400]
# axis轴
# axis=0是上下合并  
# axis=1是左右合并 
# 级联需要将图片的像素切成相同的
np.concatenate((nz,xg),axis=1) 
```



#### numpy.[hstack|vstack]

堆 做级联

分别代表水平级联与垂直级联,填入的参数必须被小括号或中括号包裹

vertical垂直的 horizontal水平的 stack层积

这两个函数的值也是一个list或tuple

```
np.vstack((nz,xg)) # 垂直级联 效果与级联axis=0相同
np.hstack((nz,xg)) # 水平级联 效果与级联axis=1相同
```



#### 副本

所有赋值运算不会为ndarray的任何元素创建副本。对赋值后的对象的操作也对原来的对象生效。

可使用ndarray.copy()函数创建副本

```
new_array = array_obj.copy()
```



#### ndarray的分割

split()

```
f1,f2,f3,f4=np.split(array_obj,[50,250,450], axis=1)
# 切割完返回一个列表，分别是图片切割后的部分
```



#### ndarray的聚合函数

##### 1. 求和np.sum

`ndarray.sum(axis)`,axis不写则为所有的元素求和，为0表示行求和，1表示列求和

```
np.sum(one,axis=1)
# 得到结果 array([4., 4., 4., 4., 4.])
```

##### 2.最大最小值：nd.max/ nd.min

axis不写则为所有的元素找最值，为0表示行，1表示列

会降维

```
np.max(lj,axis=-1)
np.min(lj,axis=-1)
```

##### 3.平均值:nd.mean()

会降维

```
np.mean(lj,axis=-1)
```

##### 4.其他聚合操作

```python
Function Name    NaN-safe Version    Description
np.sum    np.nansum    Compute sum of elements
np.prod    np.nanprod    Compute product of elements
np.mean    np.nanmean    Compute mean of elements
np.std    np.nanstd    Compute standard deviation
np.var    np.nanvar    Compute variance
np.min    np.nanmin    Find minimum value
np.max    np.nanmax    Find maximum value
np.argmin    np.nanargmin    Find index of minimum value 找到最小数的下标
np.argmax    np.nanargmax    Find index of maximum value 找到最大数的下标
np.median    np.nanmedian    Compute median of elements
np.percentile    np.nanpercentile    Compute rank-based statistics of elements
np.any    N/A    Evaluate whether any elements are true
np.all    N/A    Evaluate whether all elements are true
np.power 幂运算
np.argwhere(nd1<0)
```



#### 轴移动

moveaxis 可以将数组的轴移动到新的位置。其方法如下：

numpy.moveaxis(a, source, destination)  
其中：

a：数组。
source：要移动的轴的原始位置。
destination：要移动的轴的目标位置。

```
ljeye=np.moveaxis(ljeye,0,1)
```



#### 轴交换
和 `moveaxis` 不同的是，`swapaxes`可以用来交换数组的轴。其方法如下：

numpy.swapaxes(a, axis1, axis2) 
其中：

a：数组。
axis1：需要交换的轴 1 位置。
axis2：需要与轴 1 交换位置的轴 1 位置。

```
np.swapaxes(a,0,-1)
# 可以用来实现转置
```



#### 数组转置

`transpose` 类似于矩阵的转置，它可以将 2 维数组的水平轴和垂直交换。其方法如下：

numpy.transpose(a, axes=None) 

```python
array_obj.transpose()
# 等同于array_obj.T
```



#### 数组'循环'

数组元素的循环

`tile` 与 `repeat`

```
A = array([4, 0, 2, 8, 5])
np.tile(A,3) 
# 结果array([4, 0, 2, 8, 5, 4, 0, 2, 8, 5, 4, 0, 2, 8, 5])

B = array([[9],[6]])
np.repeat(B,3)
# 结果array([9, 9, 9, 6, 6, 6])
```



#### 数组检索

```
index = np.argwhere(A.ravel()<=18).ravel()
# 得到对应的位置索引

A.ravel()[index]
# 得到对应位置的值
```



#### ndarray的矩阵操作

### 1. 基本矩阵操作

1) 算术运算符：

- 加减乘

矩阵乘：np.dot(A.T,A)

矩阵的值加：np.add() 

矩阵的值乘：np.multiply() 

```
np.dot(A.T,A) # 矩阵乘法
np.add(A,B) # 矩阵对应的值相加
np.multiply() # 矩阵对应的值相乘
```



#### ndarray的排序

```
冒泡排序：数据对就会慢，反面例子
for i in range(len(A)-1):
    for j in range(len(A)-1-i):
        if A[j] > A[j+1]:
            A[j],A[j+1] =  A[j+1],A[j]
```



#### 快速'排序

np.sort()与ndarray.sort()都可以，但有区别：

- np.sort()不改变输入
- ndarray.sort()本地处理，不占用空间，但改变输入

```
A.sort(kind='quicksort') # 选择排序
```

```
快速排序的实现代码
def Quicksort(mylist,start,end):
    if start < end:
        i,j = start,end
        #设置基准
        base = mylist[start]
        #小左大右
        while i<j:
            #0<9
            #[6, 3, 3, 1, 1, 4, 5, 8, 8, 5]
            while (i<j) and (mylist[j] >= base):
                j -= 1
            #[5, 3, 3, 1, 1, 4, 5, 8, 8, 5]
            mylist[i] = mylist[j]
            
            #0<9
            # #[5, 3, 3, 1, 1, 4, 5, 8, 8, 5]
            #5<=6 i=1
            #8<9
            #8<=6
            while (i<j) and (mylist[i] <= base):
                i += 1
            #[5, 3, 3, 1, 1, 4, 5, 8, 8, 8]
            mylist[j] = mylist[i]
        
        mylist[i] = base
        
        #递归
        Quicksort(mylist,start,i-1)
        Quicksort(mylist,j+1,end)
    return mylist



#3个参数
Quicksort(A,0,len(A)-1)
```



```
def Quicksort(list_):
    if len(list_) > 1:
        left = np.ndarray(0, dtype=np.int8)
        right = np.ndarray(0, dtype=np.int8)
        base = list_[0]
        list_ = list_[1:]
        for num in list_:
            if num < base:
                left = np.append(left, num)
            else:
                right = np.append(right, num)
        return np.hstack((Quicksort(left),base, Quicksort(right)))
    else:
        return list_
```











#### 部分排序

np.partition(a,k)

有的时候我们不是对全部数据感兴趣，我们可能只对最小或最大的一部分感兴趣。

- 当k为正时，我们想要得到最小的k个数
- 当k为负时，我们想要得到最大的k个数

```
np.partition(A,5)
# 取5个最小的值，放在开头。后面的序列不管。

np.partition(A,-5)
# 取5个最大的值，放在结尾。前面的序列不管。
```



### matplotlib

引入：

```python
import  matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
```

##### 目录
一、【重点】Matplotlib基础知识

二、设置plot的风格和样式

1、【重点】点和线的样式
2、X、Y轴坐标刻度
三、2D图形
1、示例
2、【重点】直方图
3、【重点】条形图
4、【重点】饼图
5、【重点】散点图
6、【重点】3D图

下面的自学
四、图形内的文字、注释、箭头

1、图形内的文字
2、注释
3、箭头
五、玫瑰图



##### Seaborn的五种风格的画板

darkgrid 暗网格

whitegrid 白网格

dark 黑色

white 白色

ticks 标记

设置风格: sns.set_style()

#### 控制刻度:

sns.set_context('paper')

#### 调色板:

sns.color_palette() 设置颜色:

sns.set_palette() :设置颜色

sns.palplot() : 显示颜色

sns.hls_palette(8,l=.7,s=.8) :设置圆形画板色,l是亮度,s是饱和度

plt.plot() ：画出函数

```python
sns.set_style('dark') # 设置画板为暗色（灰灰的）只设置，不显示
plt.plot() # 显示画板

sns.color_palette('hls',100) # 设置100种颜色，hls是一只色彩集
sns.hls_palette(n_colors=7,l=0.6, s=0.7) # 实现的功能相同
```

##### 线形图

```
#二维的图
x = np.linspace(-5,5,100)
y = 0.5*x
plt.plot(x,y)

# 斜率为0.5的直线

#曲线
x = np.linspace(-5,5,100)
#exp是以e为底数的指数函数
y = np.exp(-x**2)
plt.plot(x,y)


#正、余弦函数
x = np.linspace(-5,5,100)
y = np.sin(x)
y1 = np.cos(x)
plt.plot(x,y) # 画出正弦曲线图
plt.plot(x,y1) # 画出余弦曲线图

# 一个多项式
x = np.linspace(0,14,100)
for i in range(1,100):
    plt.plot(x,np.exp(-x+i*0.5))

# 另一个多项式
x = np.linspace(-14,14,100)
y = 5*x**2+x**4-3.5
plt.plot(x,y)
plt.grid(color='hotpink',alpha=.5,axis='both')
plt.axis('off') # 去除轴，只显示曲线

# 圆形
x = np.linspace(-1,1,100)
y = (1-x**2)**.5
plt.plot(x,y,x,-y)
plt.axis('image') # 压缩的意思

x = np.linspace(-1,1,100)
y = (1-x**2)**.5
plt.plot(x,y,x,-y)
plt.axis('equal') # 压缩的意思 
```

##### 图片的标题

```
x = np.linspace(-1,1,100)
y = (1-x**2)**.5
plt.plot(x,y,x,-y)
plt.axis('equal') 
plt.title('this is circle',color='purple',fontsize=20)
# 添加标题

plt.xlabel('X',color=(0.35,0.5555,0.11111),fontsize=20,rotation=0)
#rotation中 所有角度全是基于x轴
plt.ylabel('f(x)=(1-x^2)^.5',color='blue',fontsize=20,rotation=90)
```

##### 添加图例

```
x = np.linspace(-5,5,100)
y = np.sin(x)
y1 = np.cos(x)
plt.plot(x,y,label='sin') # label表示添加标签
plt.plot(x,y1,label='cos')

plt.legend() # 显示图例
--------------------------------------------------
x = np.linspace(0,14,100)
for i in range(1,100):
    plt.plot(x,np.sin(x+i*.5)*(7-i),label=i)
#location表示位置，对x和y轴的偏移倍数
# ncol 表示显示的行数
plt.legend(loc=[0,1],ncol=11)
```

##### 点和线的风格设置

```
x = np.linspace(-5,5,10)
y = np.sin(x)**2
# plt.plot(x,y,marker='o') #圆点（简单，可识别度高，一般都用这个）
# plt.plot(x,y,marker='s')
# plt.plot(x,y,marker='d')
# plt.plot(x,y,marker='x')

#figure身材(结点)
plt.figure(figsize=(10,6))
# plt.plot(x,y,marker='o',markersize=20,ls='--')
plt.plot(x,y,marker='o',markersize=20,ls='steps')
------------------------------------------------------
x1 = np.linspace(0,10,100)
x2 = np.linspace(1,11,100)
y1 = 3*x1**2 - 2
y2 = 1.5*x2**2 - 1.1
plt.plot(x1,y1,x2,y2)
# 计算相关系数的
```

##### 刻度映射

```
#1.设置画布对象
#1.代表的行数 2.列数 3.画布的编号(默认从1开始,不能为0)
axes = plt.subplot() # 创建画布对象，使用对象调用plot函数，进行绘画
x = np.linspace(-np.pi,np.pi,100)
y = np.sin(x)
axes.plot(x,y,ls=':',lw=10)
pi = np.pi
#set_xticks 重新设定刻度值
axes.set_xticks([-pi,-pi/2,0,pi/2,pi])
#映射刻度  lateX
axes.set_xticklabels(['$-\pi$','$-\pi/2$',0,'$\pi/2$','$\pi$'],fontsize=20)

axes.set_yticks([-1,0,1])
#映射刻度  lateX
axes.set_yticklabels(['min',0,'max'],fontsize=20)
```



#### 直方图

需要的数据是一维的,统计数据中每个元素出现的次数

hist()

```
a = np.random.randint(0,10,20)
# bins越大间隔越大，观察越清晰，但是太大数据图就会太小，细节自己掌握
plt.hist(a,bins=20)
--------------------------------------
a = ['a','a','b','c','d']
plt.hist(a)
#可以直观的体现投票
```

seaborn中的直方图：

不支持离散数据（如字符串）

```
#sns中的直方图不支持离散类型
#数字类型是连续的   字符串是离散的
sns.distplot(a,bins=20)
#电商 卖家 :一个店铺中，n多商品 , 那个商品买的最好
```



#### 柱状图

二维的,一般和时间捆绑在一起

```
titanic = sns.load_dataset('titanic') # sns自带的数据集
sns.barplot(x='sex', y='survived', hue='pclass', data=titanic)
# seaborn中的柱状图色彩更丰富，一般都会使用这个来显示柱状图
---------------------------
date = ['2012','2013','2014','2015','2016']
GDP = [12,6,14,7,16]
#每年12个月 利润 或者是 出货量   5-10           11.11  12.12  1  2
#计算各个省份的GDP
plt.bar(date,GDP)
# plt中的柱状图只显示蓝色的，吸引力不够，多不用
```

#### 饼图

一维的

```
a = np.array([.1,.2,.35])
plt.pie(a)
plt.axis('image')
# 数据按比例划分，不足1会按比例出现空白

labels = ["sh",'bj','sz','gz','hz','nb','sz','wx','cd','qd']
gdp = [10000,9900,9400,6000,8000,7000,8001,5000,7000,4000]
expload=[.2,0,0,0,0,0.1,0,0,0,0]
# labels添加注释（标题），autopct在饼图上添加具体比例，
# explode显示重点，colors替换色彩
plt.pie(gdp,labels=labels,autopct='%.2f%%',explode=expload,colors=sns.color_palette('rainbow',10))
plt.axis('equal')
```



#### 箱图

查看数据的离散度，直观的看到异常值

```
a = np.random.randn(10,3)
sns.boxplot(a)
```

#### 散布图

观察数据的分布情况和聚集度或者叫相似度

2维,一列代表一个轴

scatter()

```python
from sklearn.datasets import load_iris
iris = load_iris() # 野百合（鸢尾花）
data = iris.data
target = iris['target']
# c= class 是一个必须的参数，不然不能区分各点之间的差异
plt.scatter(data[:,1],data[:,3],c=target,cmap='rainbow')
```

```python
import pandas as pd
# frame
d=pd.DataFrame(data)
sns.boxplot(data=d)

```

#### 散布密度图

```python
# kind表示种类，hex表示蜂巢图，其他参数：scatter" | "reg" | "resid" | "kde" 

sns.jointplot(data[:,0],data[:,1],kind='hex')
```

#### 回归散布图

```
sns.regplot(data[:,2],data[:,-1])

```

#### 散布图矩阵

```python
sns.pairplot(d) 
```

```
关于正态分布：
mean_ = data[:,1].mean()
std_  = data[:,1].std() 
mean_ - 3*std_
mean_ + 3*std_ 
data[:,1] < (mean_ - 3*std_) # 区间外的判断
```

### 基于sql的数据分析

```python
import pandas as pd
from sqlalchemy import create_engine

# 使用pandas读取csv文件（第一行自动认为是头标，如果不是需要定于header参数，并使用names添加列名）
userinfo = pd.read_csv('user_info_utf.csv',header=None,names=['userid','sex','birth'])

# 同上，读取文件，设置参数
orderinfo = pd.read_csv('order_info_utf.csv',header=None,names=['orderid','userid','ispaid','price','paidtime'])

# 使用sqlalchemy进行数据库连接，返回一个连接对象
conn = create_engine("mysql+pymysql://root:123456@localhost:3306/python?charset=utf8")

# 将读取到的数据写入数据库中
#name = table
#con 连接对象
userinfo.to_sql(name='user_info',con=conn,index=False)
orderinfo.to_sql('order_info',conn,index=False)
```

```mysql
sql语句与实现的查找功能：
# 统计不同月份下单的人数
#思路：ispaid='已支付'  然后对月份分组  对用户去重
select month(paidtime) as 月份,count(distinct userid) as 用户数量 from order_info where ispaid='已支付' group by 月份;

# 统计三月的复购率
#思路: 月份=3   ispaid='已支付'  在筛选除订单>1
#54799 代表3月份的购买总人数
select concat((count(userid)/54799)*100,'%') from (select month(paidtime) ,userid,count(userid) as uc from order_info where month(paidtime)=3 and ispaid='已支付' group by userid having count(userid)>1) as new;

# 统计三月份的复购率 和 复购用户数
select concat((count(userid)/54799)*100,'%') as 复购率 ,count(userid) as 复购数 from (select month(paidtime) ,userid,count(userid) as uc from order_info where month(paidtime)=3 and ispaid='已支付' group by userid having count(userid)>1) as new;
select concat((count(if(uc>1,1,null))/54799)*100,'%') as 复购率,count(if(uc>1,1,null)) from  (select month(paidtime) ,userid,count(userid) as uc from order_info where month(paidtime)=3 and ispaid='已支付' group by userid) as new;

# 求每个月的购买用户数和复购用户数
#思路:月份必须要分组
select md as 月份,count(if(uc>1,1,null)) as 复购用户数,count(userid) as 每个月的购买数,(concat((count(if(uc>1,1,null))/count(userid))*100,'%')) as 复购率 from (select userid,month(paidtime) as md,count(userid) as uc from order_info where ispaid='已支付' group by month(paidtime),userid) as new group by md;

# 对导入数据库中的数据表进行字段修改:
# 追加索引：
alter table `order_info` add primary key(`orderid`);
alter table `order_info` modify `orderid` int primary key auto_increment;
alter table `order_info` modify `userid` int;
alter table `order_info` add index `uid`(`userid`);
alter table `order_info` modify `ispaid` char(32);
alter table `order_info` add index `ipd`(`ispaid`); 
alter table `order_info` modify `price` float;
alter table `order_info` add index `pic`(`price`); 
alter table `order_info` modify `paidtime` datetime;
alter table `order_info` add index `pt`(`paidtime`); 

alter table `user_info` modify `userid` int primary key auto_increment;
alter table `user_info` modify `sex` enum('男','女');
alter table `user_info` add index `sex`(`sex`);
alter table `user_info` modify `birth` datetime;
alter table `user_info` add index `bt`(`birth`); 

# 最常用的索引是普通索引当中的联合索引

# 用空间换时间

# 回购率
# 上个月买过，这个又买了
# 4月份的回购率

#查询上个月的下单的用户54799  和 本月对比  

select concat((count(distinct userid)/54799)*100,'%') as 回购率  from order_info where ispaid='已支付' and month(paidtime)=4 and userid in (select distinct userid from order_info where ispaid='已支付' and month(paidtime)=3);

# 计算每个月的回购率
# 思路 月份要分组 多条sql语句 
select t1.m as 月份,count(t1.m) as 用户数,count(t2.m) as 回购的用户数,concat((count(t2.m)/count(t1.m))*100,'%') as 回购率 from (select userid,date_format(paidtime,"%Y-%m-01") as m from `order_info` where ispaid='已支付' group by userid,date_format(paidtime,"%Y-%m-01")) as t1
left join
(select userid,date_format(paidtime,"%Y-%m-01") as m from `order_info` where ispaid='已支付' group by userid,date_format(paidtime,"%Y-%m-01")) as t2
on t1.userid=t2.userid and t1.m = date_sub(t2.m,interval 1 month) group by t1.m;


# 统计3个月内男女的消费频率
#性别分组 消费订单的数量
select sex as 性别,avg(ct) as 平均消费次数 from (select s.userid,count(s.userid) as ct,sex from order_info as o  inner join (select * from user_info where sex <> '' and sex is not null) as s on o.userid = s.userid where ispaid='已支付' group by sex,o.userid) as new group by sex;

# 题目：
#1.所有人平均消费间隔
#2.环比
#3.消费二八法：消费的前二十
#4.总消费
```



### pandas

#### Series

Series是一种类似与一维数组的对象，由下面两个部分组成 :

value: 一组数据

key：相关的数据索引标签



##### 1）Series的创建

两种创建方式：

(1) 由列表或ndarray数组创建

`默认索引为0到N-1的整数型索引`

```
# index参数
# list会将字符串强转为列表，列表的每一个值，对应一个索引index
b = pd.Series(range(1,6),index=list('abcde'))

# name参数
# name是为了dataframe做准备
c = pd.Series(data=range(5),name='id')
```

（2）由字典创建

```
pd.Series(dict(a=1,b=2))
# 各参数不再介绍
```

##### 2）Series的索引和切片

可以使用中括号取单个索引（此时返回的是元素类型），或者中括号里一个列表取多个索引（此时返回的仍然是一个Series类型）。分为显示索引和隐式索引：

(1) 显式索引：

```
- 使用index中的元素作为索引值
- 使用.loc[]（推荐）
```

可以理解为pandas是ndarray的升级版,但是Series也可是dict的升级版

注意，此时是闭区间

(2) 隐式索引：

```
- 使用整数作为索引值
- 使用.iloc[]（推荐）
```

注意，此时是半闭区间

```
a['a']
#关联型索引    离散的

a[0]
#枚举型索引    连续的

#切片 半闭
a[0:4]

#切片 闭区间
a["a":"e"]

#显式索引 只能使用 关联索引
a.loc['b':'d']

#隐式索引 半闭区间
a.iloc[0:-1]
```

3）Series的基本概念

可以把Series看成一个定长的有序字典

可以通过shape，size，index,values等得到series的属性

```
a.shape # 形状
a.size # 总量
a.index # 查看索引
a.values # 查看值
a.ndim # 查看维度（只能是1维）
a.dtype # 查看存储类型
```

```
a.astype(np.int16)
# 修改存储类型

a.keys()
# 得到键（索引）


a.head()
a.tail()

可以通过head(),tail()快速查看Series对象的样式
共同都有一个参数n，默认值为5

使用pandas读取CSV文件
pd.read_csv('./file_path')

使用pandas读取sql
# sql表示sql语句，con表示数据库连接
pd.read_sql(sql,con)
pd.read_sql_query(sql,con)

```

当索引没有对应的值时，可能出现缺失数据显示NaN（not a number）的情况

可以使用pd.isnull()，pd.notnull()，或自带isnull(),notnull()函数检测缺失数据

```
#如何剔除值为空的
index = pd.notnull(a)
a[index]

#如何查找值为NaN的索引
s = pd.isnull(a)
a[s].index

```

4）Series的运算
(1) 适用于numpy的数组运算也适用于Series

```
pd.Series([1,2,3])+pd.Series([3,2,1])

```

(2) Series之间的运算
在运算中自动对齐不同索引的数据
如果索引不对应，则补NaN
注意：要想保留所有的index，则需要使用.add()函数

```
pd.Series([1,2,3]).sum()
pd.Series.add(self, other, level=None, fill_value=None, axis=0)
```

#### DataFrame

DataFrame是一个【表格型】的数据结构，可以看做是【由Series组成的字典】（共用同一个索引）。DataFrame由按一定顺序排列的多列数据组成。设计初衷是将Series的使用场景从一维拓展到多维。DataFrame既有行索引，也有列索引。

行索引：index
列索引：columns
值：values（numpy的二维数组）
我们的 训练集（一些二维的数据）都是二维的，那么Series满足不了这个条件,xy轴，轴上的一点（0，0）

```
df = pd.DataFrame(data=np.random.randint(1,10,(5,4)),columns=list('ABCD'),index=list('金木水火土'))

```

1）DataFrame的创建
最常用的方法是传递一个字典来创建。DataFrame以字典的键作为每一【列】的名称，以字典的值（一个数组）作为每一列。

此外，DataFrame会自动加上每一行的索引（和Series一样）。

同Series一样，若传入的列与字典的键不匹配，则相应的值为NaN。

`pd.DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)`

```
#行 代表的样本数量  列 代表 特征的数量
df.shape
df.ndim
df.values
df.index   #行索引
df.columns  #列索引
df.dtypes

df.A = df['A'].astype(np.int8)

```

2）DataFrame的索引
(1) 对列进行索引

- 通过类似字典的方式
- 通过属性的方式
可以将DataFrame的列获取为一个Series。返回的Series拥有原DataFrame相同的索引，且name属性也已经设置好了，就是相应的列名。

(2) 对行进行索引
- 使用.loc[]加index来进行行索引
- 使用.iloc[]加整数来进行行索引
同样返回一个Series，index为原来的columns。

(3) 对元素索引的方法¶
- 使用列索引
- 使用行索引(iloc[3,1]相当于两个参数;iloc[[3,3]] 里面的[3,3]看做一个参数)
- 使用values属性（二维numpy数组）

使用行索loc引切片

`df.loc[index:index2]`

使用隐式iloc

`df.iloc[num:num2]`



3）DataFrame的运算
（1） DataFrame之间的运算
同Series一样：

在运算中自动对齐不同索引的数据
如果索引不对应，则补NaN

2） Series与DataFrame之间的运算
【重要】

使用Python操作符：以行为单位操作（参数必须是行），对所有行都有效。（类似于numpy中二维数组与一维数组的运算，但可能出现NaN）

使用pandas操作函数：

  axis=0：以列为单位操作（参数必须是列），对所有列都有效。
  axis=1：以行为单位操作（参数必须是行），对所有行都有效。

##### pandas 中对于空的操作

- isnull()
- notnull()
- dropna() #过滤空值
- fillna() #填充空值

```
df.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)

df.fillna(value=None, method=None, axis=None, inplace=False, limit=None, downcast=None, **kwargs)
```

#### pandas层次化索引

1. 创建多层行索引
1) 隐式构造
最常见的方法是给DataFrame构造函数的index参数传递两个或更多的数组

Series也可以创建多层索引

```
s = pd.Series(data=range(6),index=[list('aabbcc'),list('甲乙甲乙甲乙')])
#显式索引
s.loc['a','甲']

#多级索引不对隐式产生效果
s.iloc[3]
```

 DataFrame建立2级列索引 

1）直接写

```
df = pd.DataFrame(data=np.random.randint(0,100,(4,6)),columns=[['数学','数学','英语','英语','语文','语文'],['期中','期末','期中','期末','期中','期末']],
index=['贾亮','王强','陈凡','李晶'])

```

2) 显示构造pd.MultiIndex

```
# 使用数组
df1 = pd.DataFrame(data=np.random.randint(0,100,(4,6)),
                  columns=pd.MultiIndex.from_arrays([['数学','数学','英语','英语','语文','语文'],['期中','期末','期中','期末','期中','期末']]),
                  index=[list('蓝蓝绿绿'),['贾亮','王强','陈凡','李晶']])

# 使用tuple
df2 = pd.DataFrame(data=np.random.randint(0,100,(4,6)),columns=pd.MultiIndex.from_arrays([['数学','数学','英语','英语','语文','语文'],['期中','期末','期中','期末','期中','期末']]),index=pd.MultiIndex.from_tuples([('蓝','PGTWO'),('蓝','宋鸡'),('绿','李三日'),('绿','蒋人韦')]))

# 使用product,最简单，推荐使用
df3 = pd.DataFrame(data=np.random.randint(0,100,(4,6)),columns=pd.MultiIndex.from_product([['数学','英语','语文'],['期中','期末']]),index=pd.MultiIndex.from_product([['蓝','绿'],['甲','乙']]))
```

2.多层列索引+行索引
除了行索引index，列索引columns也能用同样的方法创建多层索引

3.多层索引对象的索引与切片操作
1）Series的操作
【重要】对于Series来说，直接中括号[]与使用.loc()完全一样，因此，推荐使用中括号索引和切片。

(1) 索引

```
df3.iloc[1:-1]
df3.loc["蓝","甲"]
df3.loc["蓝","数学"]

```

2）DataFrame的操作
(1) 可以直接使用列名称来进行列索引

(2) 使用行索引需要用ix()，loc()等函数

【极其重要】推荐使用loc()函数

注意在对行索引的时候，若一级行索引还有多个，对二级行索引会遇到问题！也就是说，无法直接对二级索引进行索引，必须让二级索引变成一级索引后才能对其进行索引！

4.索引的堆（stack）
stack()
unstack()

```
#列索引转变为行索引
df.stack()

#行索引转变为列索引
df.unstack()

```

5. 聚合操作
【注意】

需要指定axis

【小技巧】和unstack()相反，聚合的时候，axis等于哪一个，哪一个就保留。

所谓的聚合操作：平均数，标准差,方差，最大值，最小值……

```
# 平均值
df.mean()

# 标准差 数据的波动性 
df1.std()

# 方差
df1.var()
```

#### pandas的拼接操作
pandas 和 mysql 非常的相似,

mysql可以对数据进行统计

pandas主要作用就是对数据进行一个统计 pandas 也有类似于 left join 的操作 select union select

```
回顾numpy的级联
a = np.random.randint(0,100,(5,4))
b = np.random.randint(0,100,(5,4))
np.concatenate((a,b),axis=1)

A = pd.DataFrame(a)
B = pd.DataFrame(b)
pd.concat((A,B),axis=1)

```

##### 使用pd.concat()级联
pandas使用pd.concat函数，与np.concatenate函数类似，只是多了一些参数：

`pd.concat(objs, axis=0, join='outer', join_axes=None, ignore_index=False,keys=None, levels=None, names=None,verify_integrity=False,copy=True)`

简单级联

 和np.concatenate一样，优先增加行数（默认axis=0） 

```
# 内连接，axis=1只对相同的行进行级联
pd.concat([df1,df2],axis=1,join='inner')
# 内连接，axis=0对相同的列进行级联
pd.concat([df1,df2],axis=0,join='inner')

# 注意index,columns在级联时可以重复

# 也可以选择忽略ignore_index，重新索引，行索引重置
pd.concat([df1,df2],axis=0,join='inner',ignore_index=True)
```

#### 连接mysql获取数据

```python
import pymysql
import pandas as pd
conn = pymysql.connect(host="localhost",port=3306,user='root',passwd='123456',db='python')
#游标
cursor = conn.cursor(cursor=pymysql.cursors.DictCursor)
#查询
cursor.execute("select * from user_info limit 10")

userinfo = cursor.fetchall()

cursor.close()
conn.close()
pd.DataFrame(userinfo)

# 更简单的方式
from sqlalchemy import create_engine
conn = create_engine("mysql+pymysql://root:123456@localhost:3306/python")
sql = "select * from user_info limit 10"
userinfo=pd.read_sql_query(sql,conn)


sql = "select * from order_info where userid<11"
orderinfo=pd.read_sql_query(sql,conn)

```

2) 不匹配级联
不匹配指的是级联的维度的索引不一致。例如纵向级联时列索引不一致，横向级联时行索引不一致

有3种连接方式：

外连接：补NaN（默认模式）

 内连接：只连接匹配的项 

`join='inner'`

 连接指定轴 join_axes 

```
pd.concat([userinfo,orderinfo],axis=0,join_axes=[userinfo.columns])
```

3) 使用append()函数添加
由于在后面级联的使用非常普遍，因此有一个函数append专门用于在后面添加

append 和 concat 相似

```
userinfo.append(new)

```

2.使用pd.merge()合并
merge与concat的区别在于，merge需要依据某一共同的行或列来进行合并

使用pd.merge()合并时，会自动根据两者相同column名称的那一列，作为key来进行合并。

注意每一列元素的顺序不要求一致

1) 一对一合并

2) 多对一|一对多合并

3) 多对多合并

4) key的规范化

将id设置为行号:set_index() `userinfo.set_index(keys='id',inplace=True)`

5) 内合并与外合并
内合并：只保留两者都有的key（默认模式）
外合并 how='outer'：补NaN
左合并、右合并：how='left'，how='right'

`pd.merge(userinfo,orderinfo,left_index=True,right_index=True)`

```
#导入文件
abb = pd.read_csv('./state-abbrevs.csv')
are = pd.read_csv('./state-areas.csv')
pop = pd.read_csv('./state-population.csv')

# 修改字段的列索引
pop_col = pop.columns.tolist()
pop_col[0] = 'state_region' # 修改第一个字段
pop.columns = pop_col

# 合并两个dataframe
pop_abb = pd.merge(pop,abb,left_on='state_region',right_on='abbreviation',how='outer')

#空值检测
pop_abb.isnull().sum()
#删除空值比较多的冗余列
pop_abb.drop('abbreviation',axis=1,inplace=True)

#哪一些州名缺失了  #Puerto Rico
cond = pop_abb.state.isnull()
pop_abb['state_region'][cond].unique()
cond_pr = pop_abb.state_region == 'PR'
pop_abb['state'][cond_pr] = 'Puerto Rico'
cond_usa = pop_abb.state_region == 'USA'
pop_abb['state'][cond_usa] = 'United States of America'
#query查询  where
res_2000_pr = pop_abb.query("year=='2000' & state_region=='PR'")
total = res_2000_pr.iloc[0].population
under18 = res_2000_pr.iloc[1].population
#先填补under18
cond_pop = pop_abb.population.isnull()
cond_2 = pop_abb[cond_pop].ages == 'under18'
#cond_2是基于pop_abb[cond_pop]

new_under18 = pop_abb[cond_pop][cond_2]

new_under18.population = under18

#先找到对应于原对象的行索引
indexs = pop_abb[cond_pop][cond_2].index

pop_abb.loc[indexs] = new_under18
#填补total
cond_3 = pop_abb[cond_pop].ages == 'total'
new_total = pop_abb[cond_pop][cond_3]

new_total.population = total

#先找到对应于原对象的行索引
indexs = pop_abb[cond_pop][cond_3].index

pop_abb.loc[indexs] = new_total

pop_abb_are = pd.merge(pop_abb,are,how='outer')
pop_abb_are.isnull().sum()
#替换列名
cols = pop_abb_are.columns.tolist()
cols[-1] = 'area'
pop_abb_are.columns = cols
#筛选谁的面积是空缺的
cond_are=pop_abb_are.area.isnull()
pop_abb_are['state'][cond_are]
#美国的面积怎么计算？
usa_area = pop_abb_are.query("year=='2012' & ages=='total' & state_region!='USA'").area.sum()
new = pop_abb_are.query("state_region=='USA'")
indexs = new.index
new.area = usa_area
pop_abb_are.loc[indexs] = new

#查找2010年各州  未成年人数 和  成年人数
u18 = pop_abb_are.query("year=='2010' & ages == 'under18'").population
g18 = pop_abb_are.query("year=='2010' & ages == 'total'").population - u18
#计算各州2012年的人口密度
#找出2012人口密度比较大的前5各州
#sort_values()
```



### 数据处理

数据清洗:

- 1.空值过滤
- 2.去除重复数据
- 3.数据的合并
- 4.分组
- 5.排序
- 6.重采样
- 7.离散化和分箱
- 8.映射

#### 去除重复的数据

可以使用 duplicated() # 查找重复的数据

或者使用drop_duplicates()

```
df = pd.DataFrame(dict(姓名=['洪香平','李晶','宋小宝','李晶','武大郎'],编号=[1,2,3,2,4]))
res = []
for i in range(len(df)):
    a,b=df.loc[i]
    str_ = str(a)+'-'+str(b)
    res.append(str_)
set_ = set(res)
for n in res:
    if n in set_:
        print(False, n)
        set_.remove(n)
    else:
        print(True,n)
#每一行中的每一列数据完全一致算重复数据
#如何获取重复数据的索引
#dtypes ndim  T shape columns  index
drop_cond = df.duplicated()
drop_index=df.loc[drop_cond].index
df.drop(labels=drop_index,axis=0,inplace=True)
#行索引的范围就是样本数量的范围
df.index = range(len(df))

# 去重
df.drop_duplicates()
```

#### 映射

- map() apply()  transform() 三个映射函数
- replace() 替换DataFrame中的值
- rename()  替换行索引

```
# 创建一个有脏数据的dataframe
df = pd.DataFrame(dict(汽车品牌=['夏利','奥拓','五菱','众泰','时风'],价格=[10000,'?',50000,100000,np.nan]))
#to_replace=dict()  替换无用数据
dict_ = {'?':np.nan,'??':np.nan,'&':np.nan} # 规定兑换规则
df.replace(dict_,inplace=True)
```

##### rename

#替换行索引

```
#mapper=dict()  数据可以多，不能少，多余的无用
index = {0:'郭靖',1:'虚竹',2:'无名',3:'独孤求败',4:'风清扬',5:'琦玉',6:'火云邪神'}
df.rename(index)
```

##### map

```
df = pd.DataFrame(data=np.random.randint(10,100,(5,3)),index=list('东南西北中'),columns=['化学','地理','生物'])

def create(item):
    if item<60:
        return '渣渣'
    elif item>79:
        return '学霸'
    else:
        return '混子'

def change(item):
    unq = df.sex.unique()
    for i in range(len(unq)):
        if item == unq[i]:
            return i

# 添加一列
df['评估']=df['化学'].map(create)
df['sex'] = list('男男女女男')

df['sex'] = df.sex.map(change) 使用函数进行替换

# 也可以使用字典替换
d={0:'男',1:'女'}
df['sex'] = df.sex.map(d)
```

##### 异常检测



```python
df = pd.DataFrame(data=np.random.normal(loc=90,scale=30,size=(50,3)),columns=['化学','地理','生物'])
df.describe() # 查看总数，平均值，标准差，最大最小四分值

df.plot(kind='box') # 箱图查看异常值
```

#### 数据的聚合

- 分组
- 函数处理
- 合并

```python
df = pd.DataFrame({"小贩":['李静','李静','李静','姜大妈','姜大妈','姜大妈','喵大爷','喵大爷','喵大爷','喵大爷'],
                  "蔬菜":['秋葵','大蒜','韭菜','金针菇','木耳','秋葵','大蒜','韭菜','金针菇','木耳'],
                  "价格":np.random.randint(10,25,10)})

# 蔬菜种类分组，查看每种蔬菜的价格数量
df.groupby(by=['蔬菜']).价格.count()

#找到每种蔬菜价格的最小值
df.groupby(by='蔬菜').价格.min()

# 可以在transform中使用聚合函数
#查找每一种蔬菜的均值，然后把均值添加为一列
# map函数不能被Groupby对象调用
df['均值']=df.groupby(by='蔬菜').价格.transform(np.mean)
a=pd.DataFrame(df.groupby(by='蔬菜').价格.apply(np.mean)) # 强转一下
pd.merge(df,a,left_on='蔬菜',right_index=True).sort_index() # 将价格列加上
```

#### 离散化和分箱

- 数字类型,普遍是连续的
- 字符串类型,离散的
- 时间类型，一般认为是连续的。

pd.cut()数据离散化

```
# 读取美国选举数据
usa = pd.read_csv('usa_election.csv')
# 参选人
usa.cand_nm.unique()
# 总捐款数
usa.contb_receipt_amt.sum()

#pd.cut()自带遍历
#bins  范围必须是一个序列类型
bins=[0,1,10,100,1000,10000,100000,1000000,10000000,100000000]
# 添加一个分箱列
usa['contb_receipt_amt_cut'] = pd.cut(usa.contb_receipt_amt,bins)
```

#### 重采样

降采样(频度变换),把日的数据转变为月的数据。

resample() 要求行索引是时间序列类型

```
usa.contb_receipt_dt = pd.to_datetime(usa.contb_receipt_dt)

#行索引
usa.set_index(keys='contb_receipt_dt',inplace=True)
# 只查询两个有力的参选人
data = usa.query("cand_nm=='Obama, Barack' | cand_nm=='Romney, Mitt'") 

#投票数量进行统计
#rule D天 M月 Y年
#select count(amt) from data group by cand_nm;
vs_month = data.groupby(by='cand_nm').resample('M')['contb_receipt_amt'].count().unstack(level=0)

#绘制
vs_month.plot(kind='area',figsize=(32,10),alpha=0.5)
#dpi清晰度
plt.savefig('vs_month.jpg',dpi=100)

#分析每个州两个候选人分别投了多少票
vs_state = data.groupby(by=['cand_nm','contbr_st'])['contb_receipt_amt'].count().unstack(level=0)

vs_state.fillna(value=0,inplace=True)

#堆叠图 是一个比例
state_rate=vs_state.div(vs_state.sum(axis=1),axis=0)
# 改变显示方向
state_rate.plot(kind='bar',figsize=(32,16),stacked=True)
```

## numpy函数

```
常量：
	np.e # 2.718281828……自然对数
	np.pi # 圆周率
ndarray的属性：
    shape # 数组的形状
    dtype # 数据类型
    buffer # 对象暴露缓冲区接口
    offset # 数组数据的偏移量
    strides # 数据步长
    order # ｛'C','F'｝，以行或列为主排列顺序
np.array() # 强转为array
array(object, dtype=None, copy=True, order='K', subok=False, ndmin=0)

np.ndarray() # 创建一个ndarray数据类型
ndarray(shape, dtype=float, buffer=None, offset=0,strides=None, order=None)

np.linspace(start=0,stop=10,num=100) #创建一个有规律的array
np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)

np.logspace(start=1,stop=10,num=10) #使用对数生成一个有规律的array
np.logspace(start, stop, num=50, endpoint=True, base=10.0, dtype=None)

ones(shape, dtype=None, order='C') # 全为1的array

zeros(shape, dtype=float, order='C') # 零矩阵

np.full(shape, fill_value, dtype=None, order='C') # 全为定值的array

np.eye(N, M=None, k=0, dtype=<class 'float'>, order='C') # 单位矩阵

np.linalg.inv(a) # 求逆矩阵、

# 随机整数
np.random.randint(low, high=None, size=None, dtype='l')


np.random.randn(10,5) # 随机正态分布

np.random.random(size=10) # 0~1 的随机值
np.random.rand(d0, d1, ..., dn) # 0~1的随机值（不需要size参数）

np.random.normal(loc=0.0, scale=1.0, size=None) # 标准方差，在loc上波动scale

np.diag(v, k=0) # 对角矩阵，只有对角线有值，可以根据k偏移

np.savetxt('jj.csv',jj[0],delimiter=';') # 保存数据到文件，每个数据以；隔开
np.loadtxt('jj.csv',delimiter=';') # 读取数据，以；分割数据

np.save('jj.npy',jj)
np.load('jj.npy')

np.log2() # 以2为底的对数
np.log() # 以np.e为底的对数
np.log10() # 以10为底的对数
np.dot(a, b, out=None) # 矩阵乘法


array_obj.var() # 标准差
array_obj.std() # 方差
array_obj.mean() # 平均值
array_obj.T 转置
```

## matplotlib.pyplot函数

```
cat=plt.imread('./cat.jpg') # 读取图片
plt.imshow(cat) # 展示图片
```

## pandas函数

```

```













###### 像素更改

```python
ljface = lj[90:170,200:280].copy() # 原数组不可更改，所以copy了一份
# 替换像素，改成红色（对应rgb）
ljface[15,33] = [255,0,0]
#：代表占位符
plt.imshow(ljface[:,:,::-1])
```

###### 切图

```
ljeye = ljface[24:29,8:28]
# 切片，得到局部图片
plt.imshow(ljeye)
```





#### 打马赛克原理

```python
ljcp = lj.copy() # 原图读取不可写，需要copy一份
# 使用for循环来完成打马
for i in range(4):
    for j in range(4):
        #90:170是行   200：280是列
        ljcp[90+i*20:110+i*20,200+j*20:220+j*20] = lj[90+i*20:110+i*20,200+j*20:220+j*20][::20,::20]
# 对原有的像素点进行替换，换成右下角最后一个像素点
```





