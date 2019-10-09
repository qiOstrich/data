# Linux

linux是一个操作系统，控制硬件，应用软件。

发行版：

1. redhat：最成功的的商用Linux
2. fedora：个人版的redhat
3. centos：社区版的redhat
4. debian：纯粹的自由软件构建的发行版，拥有最大的开源软件库
5. ubuntu：最受欢迎的linux发行版
6. deepin：国人制作的发行版
7. gentoo：一切从源码开始手动安装，性能超高，非常稳定
8. arch：省去编译，手动安装一切
9. elementaryos：华丽、优雅的桌面发行版，易用

## 安装虚拟机

虚拟机是一种通过软件模拟的具有完整硬件系统功能的、运行在一个完全隔离环境中的完整计算机 系统。 在虚拟机中运行程序处于完全隔离的状态，一般不会对真实系统产生影响，但会消耗很大的系统资 源。 下载地址: 

Window 版: https://download.virtualbox.org/virtualbox/6.0.10/VirtualBox-6.0.10-132072 -Win.exe 

Linux 版: https://www.virtualbox.org/wiki/Linux_Downloads 

Mac 版: https://download.virtualbox.org/virtualbox/6.0.10/VirtualBox-6.0.10-132072-OS X.dmg

## 软件的安装

1. Ubuntu下的apt命令
   - apt search application-name 搜索
   - apt show application-name 查看详情 
   - apt install application-name 安装
   - apt remove application-name 删除
   - apt autoremove 自动删除安装包

2.CentOS 下的yum命令

yum 命令与apt基本相同

1. search
2. install
3. update
4. remove

3.安装Python

​	apt install python3.7

4.安装Pycharm

​	自！己！下！去！

5.安装vnc

​	自！己！百！度！

## shell

计算机整体由软件和硬件组成，而为了能够控制硬件、使用软件，需要操作系统。

Linux就是这样的一个操作系统，操作系统需要有驱动硬件的核心Kernel，还需要有应用软件的应用Shell（壳）。

硬件Hardware计算机最底层的，也是最基础的。

核心Kernel与硬件接触。

shell(包含GUI‘用户界面’，CLI‘命令行’)和application是用户直接使用的软件。

### 常见的GUI Shell

Gnome

KDE

Xface

### 常见的CLI Shell

1. sh
2. csh
3. bash
4. zsh

可以通过 cat  /etc/shells 查看当前系统的shell

## 终端TERMINAL光标快捷键

```
CTRL + A 回到行首
CTRL + E 回到行尾
CTRL + F 左移一个字符
CTRL + B 右移一个字符
CTRL + W 删除左边的一个单词，以空格为单词间隔
CTRL + U 删除左边全部
CTRL + K 删除右边全部
CTRL + Y 恢复上一次删除的内容
CTRL + L 清屏
```



##linux的目录

```
/ 根目录
-boot 启动目录
-bin 系统二进制目录，存放普通用户的GNU命令
-sbin 系统超级二进制目录，存放管理员级别的GNU命令
-usr 资源目录(User System Resources)
	--bin 用户二进制目录，存放用户级的GNU命令
	--sbin 用户超级二进制目录，存放管理员用户的GNU命令
	--local 本地
		---bin
		---sbin
-opt 第三方开方的程序(option，选装)
-dev 设备目录
	--null 无底洞，丢弃一切写入的数据
	--zero 无限0数据流(常用来产生一个特定大小的空白文件, 或安全销毁文件)
	--shm 内存文件夹
	--random 随机数发生器
	--urandom 非阻塞的随机数发生器
-etc 系统配置文件目录
-proc 当前的进程、运行状态信息的目录
-root 管理员家目录
-home 用户的家目录
-media 媒体目录，移动媒体设备的常用自动挂载点
-mnt 挂载目录，常用手动挂载点
-lib 系统库目录，存放系统和应用的库文件
-srv 服务目录，存放本地服务的相关文件
-sys 系统目录，存放系统硬件信息的相关文件
-run 运行目录，存放系统运转时的运行数据
-tmp 临时目录，临时工作文件
-var 可变目录，存放经常变化的文件，比如日志文件

```

## 终端下目录操作

```
cd 切换文件夹目录 change directory
例：cd ./a/b/c/ 切换入当前目录中a文件夹中b文件夹中c文件夹，只输入cd进入~目录
	./ 当前目录
	../ 上级目录
	/ 根目录
	~ 用户家目录
	- 回到上次文件夹位置
pwd 显示当前目录的路径
ls 列出文件夹中的文件及文件夹list
例：ls -l ./ 当前目录的文件，列方式排序。可以缩写为ll
	-l 以列显示文件
    -lh 以友好方式显示文件
	-a 显示所有文件
	-A 显示除. ./ 外所有文件
mkdir 创建一个文件夹make directory
例：mkdir ./ a 当前文件夹中创建一个a文件夹，	mkdir -p ./a/b/c ./a/{c/{d,e}}创建多级目录。
	-p 创建多级文件夹目录
touch 创建空文件(不覆盖创建)、改变文件时间戳
例：touch file{1,2,3} ./ 在当前文件夹中创建file1 file2 file3 三个空文件
```

## 文件操作

```
echo "str" 打印字符串
echo "str"> a 在a文件中覆盖打印字符串
echo "str">> a 在a文件中追加打印字符串 
cp 复制文件 copy
例：cp ./a/file ./a/b/ 把当前文件夹中a文件夹下的file文件复制并放进b文件夹中
mv 移动文件，或更名文件
例：mv ./a ./b 把a文件或文件夹移动到b目录中，若不存在b，则a更名为b

rm 删除
```



### 文件打包压缩

#### tar打包

tar -czf filename.tar.gz  ./dir

tar -xzf filename.tar.gz

不带参数的命令不会压缩，只是打包



#### zip打包

zip -r filnename.zip ./dir

unzip filename.zip





### 文件查找find

查找当前文件夹下全部文件:   `find ./`

只查找文文件: `find ./ -type f`

只查找目录: `find ./ -type d`

只查找链接:`find ./ -type l`

按名称查找:` find ./ -name  '*.py'`

按权限查找: `find ./ -perm 0644`

按大小查找:` find ./ -size +1k -size -5k`



### md5 

md5sum pwd/filename



## 用户与组

用户有唯一的用户名，且有唯一的UID。

用户组也有唯一的名称，组也有ID，即唯一的GID。

root 用户是linux系统中权限最高的用户。UID与GID都是0。

用户名与UID等相关信息都存储在 /etc/passwd 中，可以通过命令查看:`cat /etc/passwd`

用户组与GID等相关信息存储在 /etc/group 中，可以通过命令`cat /etc/group`

在以前linux中的密码存在passwd中，现在已经全面改善。密码存在` /etc/shadow`

*passwd文件中数据: *

1. 用户名：root
2. 密码：x  早期的密码，现在已经更换
3. UID：
4. GID：
5. 注释：root 介绍此用户
6. 目录：/root
7. 用户使用的shell ：/bin/bash



*group文件格式*

1. 组名：
2. 组密码：x 以弃用
3. GID：
4. 组中成员：



*shadow文件格式*

1. 用户名：
2. 密码： 加密后的
3. 上一次修改密码的日期（day）
4. 修改密码后几天内内不能再次修改，（day）
5. 密码有效时间（day）
6. 密码失效前几天提醒（day）
7. 密码失效后宽限时间（day）
8. 账号实效日期
9. 保留字段，暂时无意义



## 用户管理

### 添加用户

useradd -D 查看添加组时的默认信息

useradd -mU -G 组 -p 密码  用户名

参数：

​	-G  新用户附加组列表

​	-m 在/home 中创建用户的家目录

​	-U 创建与用户同名的组

​	-p 加密后的密码



### 删除用户

userdel -r 用户名

​	-r 删除主目录与邮件池

### 修改用户密码

passwd 用户名 （一般需要sudo权限）



### 切换用户

su 用户名  只切换用户身份

su - 用户名  完全用这个用户进行登录，初始化用户设置



## 查看用户与组的信息

id             查看当前用户的信息

id   -u   查看uid

id   -g   查看gid

### 修改用户属性

usermod 参数 组用户名

参数：

1. -d   用户的新主目录
2. -g 强制使用group为新主组
3. -G 新的附加组列表 
4. -a 将用户追加至上边-G中提到的附加组中，其他组不会删除用户
5. -L 锁定用户账号
6. -m 将家目录移动至新目录（仅于 -d 一起使用）
7. -s 该用户账号的新登陆shell 
8. -U 解锁用户账号



## 用户组管理

### 添加组

groupadd 参数 组名

参数：

1. -g  GID
2. -p password
3. -r 创建一个系统账户



### 删除组

groupdel 组名 



## 查看登陆的用户

who 查看谁在登录

w 查看谁在登录，并显示每个登陆用户正在执行的任务

last 查看登陆历史记录

lastb 查看登陆失败记录

lastlog 查看全部用户最后一次登陆的时间



## 文件权限

在linux中文件设置了三种权限

r        read 读权限

w      write  写权限

x       execute 执行权限

使用ls -l  可以在开头看到权限的信息

其中： d 是dir文件夹     - 是file文件  l  是link链接  s是 socket

后9位是三种身份的权限： user用户自己     group 同组用户    other 其他用户

权限使用二进制存储    r=4 w=2 x=1



### 权限修改

chmod u/g/o/a   +/-/= r/w/x 文件或文件夹名

ugoa分别代表user group other  all

+表示追加权限 - 表示删除权限 = 表示赋予权限

rwx之间不需要空格或逗号



### 修改文件拥有者

chown  -R 用户：组  文件夹   将文件夹及内容数据全部转拥有着 

chown  \`id  -u\` :\` id  -g`  文件   先执行反引号中的代码可以使用$( ) 代替反引号



## 文件操作

echo 打印

echo "str" > filename              覆盖写入，或创建文件并写入

echo "str" >> filename                  追加写入,或创建文件并写入

cat                查看文件内容，会将文件加载到内存中

head -n num整数 文件名        查看文件的开头num行

tail -n num整数 文件名             查看文件结尾的num行

less                快速浏览文件，键盘控制显示：

- j             向下一行
- k           向上一行
- f            向下一页或空格
- b           向上一页或shift + 空格
- g           跳至开头
- shift g        跳至结尾
- q           退出

`sort  dir or file  `    将文本或文件升序排序

`sort -r  dir/file     `          降序排列

`uniq -N `去重，显示重复次数

`awk '{print $N}' `打印出N列

`wc` 字符统计

- -c       统计字符
- -w      统计单词
- -l        统计行

管道符       |              连接多个命令 表示按顺序执行命令





## grep文本过滤

参数：

- -i   忽略大小写
- -I  忽略二进制文件
- -r    递归查找目录
- -n   打印行号
- -c   只显示匹配到的个数
- -l   只显示匹配到的文件列表
- -o  只显示匹配道德单词
- -v 忽略制定的字段
- -E   通过正则表达式匹配
- --include='*.py'包含
- --exclude='*.js'不包含











## vim

 编辑器 有"编辑器之神"称号，简介而强大

vim 有三种模式：命令模式，插入模式，底栏命令模式

vim 文件名         打开文件编辑器

默认进入命令模式，也可以按

ESC进入命令模式

命令模式快捷键：

- h,j,k,l 光标分别左，下 ，上， 右 移动
- ctrl + e 向下滚动
- ctrl + y 向上滚动
- ctrl + f 向下翻屏
- ctrl + b向上翻屏
- ctrl +  v 列编辑  选中多列内容 x删除 Shift+i 添加按两次esc 多行添加
- yy  复制整行
- yw复制整行
- shift p 粘贴到下一行
- p 粘贴到下一行
- dd 删除整行
- dNw  删除N个单词（空格分单词）
- gg  跳至文件行首 
-  shirt + g 跳至文件结尾
- shirt +  h 跳至页首
- shirt + m 跳至页中
- shirt + l 跳至页尾
- shirt + v 选中整列
- shirt + >   向右使用空格缩进
- shirt + <     向左使用空格缩进

i 进入插入模式:

在光标处插入内容



底栏命令模式：

命令模式下输入 ： 进入底栏命令模式，输入内容：

23                 至23行

%s/asd/123/g     将全文的asd替换成123   g表示全文  %s表示替换

set nu          显示行号

set nonu        不显示行号

w                   保存

q                     退出

wq                  保存并退出

  

vim 配置文件          /.vimrc

### 备注
https://coolshell.cn/articles/5426.html
http://www.oschina.net/question/615783_148433
我的 vimrc https://raw.githubusercontent.com/seamile/rc.d/master/vimrc



## 系统状态与管理

### 进程状态

#### ps命令 process status

用于查看当时瞬间的进程状态。

ps 不带参数所提供的信息不多。只有 PID ，TTY ，TIME ， CMD，其含义将在带参数的ps中解释。

ps命令支持三种不同类型的命令参数：

unix风格，使用- ： ps -ef 

BSD风格，直接写： ps aux 

GNU 风格，使用--： ps --pid  123 

 

unix风格下：ps -ef

- -e：参数制定显示所有运行在系统上的进程

- -f：扩展输出中的参数

  显示参数：

- UID： 用户ID

- PID： 组ID

- PPID： PARENT 夫进程组ID

- C： 进程生命周期中的cpu的利用率

- STIME：进程启动时间（系统时间）

- TTY：进程启动的终端设备

- TIME：进程累计占用cpu的时间

- CMD：进程运行命令



BSD风格下 ：ps aux

- a：显示与任意终端关联的所有进程

- u：采用基于用户的格式显示

- x：显示所有的进程，包括未分配任何终端的进程

  显示参数：

- USER：

- PID：

- %CPU：

- %MEM：

- VSZ

- RSS

- TTY

- START

- TIME

- COMMAND

- STAT

  - STAT 数据含义，第一个字符及意义
    - O ： 代表正在运行 。
    - S ：代表正在休眠 。
    - R ： 代表可运行，等待cpu分配资源 。
    - Z ：僵化，进程结束，但父进程已不在 。
    - T ： 代表停止 。
  - 第二个字符及意义。
    - <：该进程处于高优先级。
    - N： 该进程处于底优先级上。
    - L ：该进程有页面锁定在内存中。
    - s ： 该进程是控制进程，一般都有子进程。
    - l ：该进程是多线程的。
    - +： 该进程运行在前台。

#### top命令

查看进程的持续状态。

头信息详解：

​	第一行，开机时长，登陆用户数，系统负载（平均：1分钟，5分钟，15分钟）。

uptime命令可以只提取这行信息。

​	第二行，任务总数，运行中的任务数，休眠中的任务数，停止数量，讲师进程数量。

​	第三行，cpu状态，按1可以显示多核。其中重点：us（用户态），sy（系统态），id（空闲）。

​	第四行，内存状态，全部，空闲，使用掉的，缓冲/缓存。

​	第五行，交换区同上。

第六行为进程详情参数：

​	PID，USER，PR， NI（NICE）， VIRT ，RES，SHR ，S， %CPU ，%MEM ，  TIME+ ，COMMAND

组ID，用户名，进程优先级，进程谦让度，占虚拟内存总量，占物理内存总量，share进程间数据交换使用的内存空间，进程状态，占cpu的比例，占内存的比例，启动时间，命令（启动的程序名）	



#### htop

更加直观，高亮设置更加人性化。

不是系统自带的命令，需要安装htop。



#### 结束进程

kill 杀死进程，或者给进程发结束信号。

  -1  平滑重启，先开新进程，再结束旧进程。

  -9  系统强制杀死进程。

  -15 给进程发结束信号（默认参数）。

pkill   processname   杀死同名进程（command）。

killall  matchedprocessname   杀死匹配到的进程。



### 内存状态 free

参数 ：

​	-m，-g：显示参数。



### 硬盘

iostat  查看硬盘写入和读取状态。

df -lh  查看硬盘分区，及诶个分区的剩余空间。

du -hs ./ 查看当前目录占用的硬盘大小。

### 网络状态

ifconfig    查看网卡状态，常用来检查自身的ip地址。interface config,接口 配置

netstat -natp 查看网络连接状态。

参数：

- -a：显示所有选项all
- -t： 显示所有与tcp相关的选项。
- -u：显示所有与udp相关的选项。
- -x：显示与unix域相关的socket选项。
- -n：拒绝显示别名，能显示数字的全部转换为数字显示。
- -p：显示建立相关连接的程序名。
- -l：显示所有状态为listen 的连接。
- -e： 显示扩展信息，如当前链接所对应的用户。
- -c：间隔一段时间执行一次netstat命令。
- -s：显示统计信息。
- -i： 间隔
- -c： 数量
- -q：安静模式，只显示结果。

lsof  

- -i:端口号  查看占用端口的程序。
- -i tcp 查看所有tcp连接
- -u abc 查看用户abc打开的所有文件
- -p 123  查看pid 123 进程打开的所有文件

路由追踪：treroute  host（ip）

DNS 查询 域名解析器：

- dig 域名     
- host 域名
- nslookup 域名



### 时间和日期

date 查看日期与时间。

cal  查看日历，有参数：

​		--one 查看本月日历。

​		--three  查看3个月的日历。

​		--year  查看全年日历。

### 下载

curl  执行http访问，也可以用来下载

wget 下载

scp 在服务器之间上传或下载 



### 服务器登陆与下载

ssh root@ip           如：ssh root@10.11.55.119 

输入登陆密码。

scp  servername@ip:pwd/filename localdir 下载。

scp  localfilepwd servername@ip:pwd/dir   上传。



### shell编程与运维

shell文件以`.sh`结尾表示shell文件

##### 注释：

shell编程中`#`井号表示注释

第一行用于著名语言,在linux中的shell脚本开头:`#!/bin/bash`

常用的有：

`#!/bin/sh`

`#!/bin/bash`

`#!/usr/bin/env bash`

python脚本的第一句一般是：`#！/usr/bin/env python`

执行shell脚本前需要给文件执行x权限：`chmod 755 shellname.sh`

使用`./shellname.sh`执行脚本

`echo $?`可以查看脚本状态码，

​	Linux 中的所有程序执行行行结束后都有状态码

​	0表示正常，其他表示有问题



#### 定义变量

`ariablename=1234`

`except ` 拥有定义全局变量

一般在定义变量时都会得到执行结果,可以使用反引号表示先执行

例子：

```
fileone=`md5sum ./dir/file | awk "{print $1}"`

这条语句表示得到file的md5加密中第一列，并用变量fileone获取
```



定义变量之间不能有空格。

使用变量需要有 `$`  ,需要美元才能用。

例子：`$ariablename`

[ command ] 条件测试命令。



### if判断

判断返回值0表示true 其他表示false



[ $n1 -eq $n2 ] 使用命令比较

[[ $n1  >  $n2 ]] 使用符号判断，只能比较单个运算符

$[$1 +$2] 用于运算 

```
if command

then

​		excute

elif command
then
​		excute

else 

​		excute

fi
```

其中fi表示结束符号



##### 比较方式：

数值比较

```
 n1 -eq n2                                 equal

-ge         										 grater equal

-gt													grater than

-le													less equal

-lt													 less than

-ne                                                   not equal

在if中：[ n1-eq n2 ]  
```

字符串

```
=         判断字符串十分相同
!=        判断两个字符串是否不同
<          
>
-n       判断字符串长度是否非0
-z       判断字符串长度是否为0，即是否为空字符串。null
```





##### 文件比较

```
-d filename        判断filename是否为目录（文件夹dir）

-e  filename        判断filename是否存在exist

-f   filename        判断filename是否为文件file

-r  filename        判断filename是否存在且可读

-w  filename        判断filename是否存在且可写

-x  filename        判断filename是否存在且可执行

-s  filename        判断filename是否存在且飞空

-O   filename        判断filename是否存在且属于当前用户 owner

-G  filename        判断filename是否存在且默认组与当前用户相同

filename -nt otherfilename                     filename是否比otherfilename新  new than

filename -ot otherfilename                      前十分比后旧 old than


```

###### 提示：

which 命令 可以查看命令的路径。



使用$可以提取变量  列子：echo " a is $a" ==> a is 1234

expr $a +$b可以执行两个变量相加或相减

$[$a *$b] 可以执行变量相乘或幂运算



### 循环语句：for

shell 中有三种循环 只教`for`

```
for 变量 in 序列
do
	需要执行的语句
done
```

```
例子：
for i in `seq 1 10`
do
		if [[ $[ $i % 2] == 0 ]]
	then
		echo "偶数: $i"
	else
		echo "奇数: $i"
	fi
done
```

1. seq \`START END\`  START，END 都是整数。语句用来产生一个数字序列
2. $[ NUM1 + NUM2 ] 语句用来进行基本的数学运算
3. [[ ... ]] 语句用来更方便的进行比较判断

也可以使用c语言风格的for循环:

```
for (( i=0; i<10; i++))
do
	需要执行的语句。
done

```





### 函数

与js中定义函数有点相同，使用function定义。

但是shell脚本中的function可以省略。

```
function foo() {
	封装的语句。
	var1=$1
	var2=$2
	
	varp=$0
	varall1=$*
	varall2=$@
}
foo para1 para2
调用不需要用括号，直接使用函数名调用，参数也按顺序写在后面，使用空格隔开。
在函数中参数使用  $  来获取参数，在脚本中也可以获得参数。

$0表示调用脚本中函数的命令名 可以用bash调用，即$0为bash 或shellname.sh 自己调用
$1  调用时的第一个参数
$2   调用时的第二个参数
……
$*  和$@ 可以获取全部参数 
$#  求和参数数量
```



#### 获取用户输入内容

```
read -p "我是提示文字" num
echo $num

-p  表示添加提示文字
```



### 命令修正：the fuck

```
thefuck
	一个终端指令修复工具
	当指令在输入错误的时候，我们可以通过fuck进行弥补
		可以提供指令修复方案
		enter
			确定
		control+c
			取消
		↑↓ 
			调整
	使用
		sudo apt update
		sudo apt install python3-dev python3-pip
		sudo pip3 install thefuck
		更新环境变量
			vim ~/.bashrc
			eval "$(thefuck --alias fuck)"
			source ~/.bashrc
```









