# 数据库系统概论

数据库是用来存储数据的。

在数据库出现之前，数据都存储在文件中，安全性极低。

### 数据库有数据模型：

1. 层次模型: 查询分类的效率比较高，但是没有的导航结构，导致分类困难，数据不完整。
2. 网状模型：没有解决导航问题，解决了数据完整性的问题。
3. 关系模型(也是现在使用的模型)：解决了之前模型存在的问题，但是效率也相对降低了。特点是：每张表都是独立的，没有导航结构；表与表之间会建立公共字段，也就将两张表之间建立了关系。



### 数据库具有行列属性

一行就是一条数据、记录。

一列就是一个字段，是表具有的属性。

字段的属性用来描述列功能。

数据的冗余：相同的数据不要多次存储！

​	冗余不可避免，只能减少。

​	冗余的存在会拖累表。

​	冗余的减小会带来表数量的增加，引起多表查询的效率下降。

### Linux数据库的开启和连接。

```
1. Ubuntu : service mysql start|stop|restart|reload|status
2. Deepin : systemctl stop|start|restart|status  mysqld
3. CentOS7 : systemctl stop|start|restart|status mysqld
4. CentOS6 : service mysqld start|stop|restart|reload|status
```





### 连接数据库

各个 Linux 系统连接数据库都一样
语法:` mysql -h loaclhost -u root -p123456 -P9876`

1. -h : host(ip地址) localhost = 127.0.0.1
2. -u : username(用户账户)
3. -p : password(密码)
4. -P : port(端口, 默认端口3306)

root是最高权限，开发中不建议使用



在mysql中输入`\q `

`quit`

`exit  `

按键`ctrl +d`

都可以退出数据库



### 密码忘记怎么办?

1. 修改配置: vim
/etc/mysql/my.cnf
2. 找到 [mysqld] 在下面添加一一句 skip-grant-tables
3. 修改完重新启动

### 数据库种类

Access  

SQL-Server 

Oracle （收费）

MySQL （应用广泛的开元数据库）

SQLite    小型数据库





## 终端操作数据库

在数据中一个语句的结束一定要使用分号；回车键一般会被忽略。

### 数据库操作

```mysql
-- 数据库都支持的备注
#   mysql独有，兼容性底
/* mysql可以识别的三种注释方式*/

mysql -h localhost -u usename (-p passsword -P端口)
# 其中-h 表示地址，也可以使用127.0.0.1  -u表示用户

create database [if not exists] `数据库名` charset=utf8mb4;    
# 创建数据库语句，其中[内容可以省略]，编码表示4字节国际编码utf-8

show databases; #查看现有数据库

use `databasename`; #使用某个数据库

alter database `databasename` charset=utf8mb4 ; #修改数据库编码，也可以是utf16

drop database [if exists] databasename;
# 删库跑路

```

### 表操作

```mysql
create table [if not exists] `tablename`(
	id int auto_increment primary key comment 'mainkey',
	name char(16) comment '你的名字' default 'your name',
	age int(4) comment '年龄' not null
)engine=myisam/innodb charaset=utf8;
# 创建表语句，其中auto_increment 表示自动生成，有这个属性一定是主键。
#    comment '是提示字' default '默认值'

show tables; #查看当前数据库现有的表

drop table [if exists] `tablename`;#删除表

desc `tablename`;
describe `tablename`; 
#都是描述表，显示表的字段和属性。

```

#### alter修改表属性

```mysql
alter table `oldname` rename `newname`;#修改表的名称

alter table `tablename` add `field` type attribute;
#增加表的字段
alter table 	`tablename` add `field` type attribute first;
#增加表的字段，并添加到第一个。
alter table 	`tablename` add `field` type attribute after filed;
#增加表的字段，并添加到指定字段的下面。

alter table `tablename` modify `field` type attr; #修改指定字段的数据类型和属性。

alter table `tablename` change `oldfield`  `newfield` type attr; #修改字段的名称和属性

alter table `tablename` change  `oldfield`  `newfield` type attr first; #当然也能同时修改位置

alter table `tablename` engine = innodb; #修改表的引擎，现多用innodb引擎还有myisam

alter table   `tablename` rename to database.tablename; #移动表至其他数据库，并改变表名

alter table  `tablename` drop `field`;
#删除表的字段
```



#### 复制表

```mysql
create table `tablename` select *from `fromtablename`;
#可以复制fromtablename中的字段和数据。但是不复制主键

create table `tablename` like `fromtablename`;
#可以复制fromtablename中的字段，但是不复制数据，主键

insert into `tablename` select  from * `fromtablename`;
#把fromtablename中的数据插入复制得到的新表

```

### 数据的增删改查

#### 增 insert

```mysql
insert into `tablename` set  field1 = values1, field2 = values2 ,field3 = values3,……; 
#给多个字段插入值。

insert into `tablenamt` (field1,field2,field3,……)  values (values1,values2,vlaues3……),(values11,values22,values33……)……; 
#使用括号对应插入多个组值。

insert into `tablename` values (values01,values02,values03,……),(values11,values12,values13,……)……；
#根据表已有的的字段插入全部对应的多组值。
```

#### 查 select

```mysql
select * from `tablename`;
#查找表中所有字段的全部数据。

select field1,field2,…… from `tablename`;
#查找表中想要的字段的全部数据。

select * from `tablename` where id = '001';
#查找id是001的所有字段的数据。
```

#### 改(更新) update

```mysql
update `tablename` set field1=values1,field2=values2,……;
#更改所有字段的信息(字段的所有的值都会改变，慎用！！！)

update `tablename` set  field1 =values1, field2 = values2,…… where field =values;
#把where中的符合字段和值的所有数据都改掉，(一般会找到精确的某一个数据)

update `tablename` set field1 =values1, field2 = values2,……  where field =values and field_o = values_o;
#给where添加多个条件，达到更精确的查找。
```



#### 删 delete

```mysql
delete from `tablename`;
#删除表中的所有数据，（必然是一个不可用操作）。

delete from `tablename` where field = values ;
#精确查找某条数据

delete from `tablename` where field in(1,2,3,4);
#删除多条数据，只要是field 与对应括号的数据相同，都会删除。

truncate `tablename`; #清空表（实际是删除表再重建）

```



#### mysql创建一个远程连接的用户并且授权

root 不可以执行远程连接

`grant all privileges on *.* to 'admin'@'%'identified by '123456' with grant
option;`

```
-- 创建新用户,并设置密码
-- *.* 代表该用户可以操作任何库、任何表
-- 主机名可以使用 '%', 代表允许该用户从任何机器登陆
GRANT ALL PRIVILEGES on *.* to 'username'@'localhost' IDENTIFIED BY "password" WITH GRANT
OPTION;
-- 刷新使权限生效
flush privileges;
```



## 字符集

#### 字符集在什么时候可以发挥作用?

1. 保存数据的时候需要使用字符集
2. 数据传输的时候也需要使用字符集
3. 在存续的时候使用字符集
1. 在MySQL的服务器上, 在数据库中, 在表的使用上, 在字段的设置上.
2. 在服务器安装的时候, 可以指定默认的字符集
2. 常⻅字符集
ASCII: 基于罗马字母表的一套字符集, 它采用1个字节的低7位表示字符, 高位始终为0。
LATIN1: 相对于ASCII字符集做了扩展, 仍然使用一个字节表示字符, 但启用了高位, 扩展了字
符集的表示范围。
GB2312: 简体中文字符, 一个汉字最多占用2个字节
GB: 只是所有的中文字符, 一个汉字最多占用2个字节
UTF8: 国际通用编码, 一个汉字最多占用3个字节
UTF8MB4: 国际通用编码, 在utf8的基础上加强了对新文字识别, 一个汉字最多占用4个字节



##### 各字符集的字符串最大字长

```
/* gbk字符集最大大字符串串⻓长度: 65535/2 -1 */
create table test(
text varchar(32766)
) charset=gbk;
/* utf8字符集最大大字符串串⻓长度: 65535/3 -1 */
create table test1(
text varchar(21844)
) charset=utf8;
/* utf8mb4字符集最大大字符串串⻓长度: 65535/4 -1 */
create table test4(
text varchar(16382)
) charset=utf8mb4;

```

##### 查看当前mysql系统支持的字符集

```
show variables like 'character_%'
```

## 校对集

在某一种字符集下, 为了使字符之间可以互相比比较, 让字符和字符形成一种关系的集合, 称之为校对集。
比如说 ASCII 中的 a 和 B, 如果区分大小写 a > B, 如果不区分 a < B;

```
create table t1(
str char(1)
) charset=utf8mb4 collate=utf8mb4_general_ci;
-- _general_ci 后缀的都是不区分大小
写的
create table t2(
str char(1)
) charset=utf8mb4 collate=utf8mb4_bin;
-- 看到后缀边是_bin的都是区分大小的/*
Linux中Mysql是区分大小的
需要自己去配置
vim /etc/my.cnf
找到[mysqld]
1是不不区分大小写,0是区分大大小小写
*/
lower_case_table_names=1
show character set; -- 查看字符集 和 校对集
show collation; -- 显示所有的校对集
```

## mysql的数据类型

### 1.整形

- tinyint  占 `1` 字节，长度：2 ** 8，256。
- smallint 占`2`字节，长度：2 ** （8\*2）,65536。
- mediumint 占`3`字节，长度 2 ** （8\*3），1677215。
- int，integer 占`4`字节，长度 2 ** （8\*4），～=42E。
- bigint  占`8`字节，长度 2 ** （8\*8），有点大。

`unsigned`表示无符号，即非负数。



### 2.浮点型

- float 占`4`字节
- double 占`8`字节
- dec(m,d) 占`m+2`个字节。
- decimal(m,d)占`m+2`个字节。
- bit(m) 1～8字节。

```
float(m,d)其中m表示总位数，d表示小数点后的位数。
double(m,d)同理
decimal(m,d)同上
```



### 3.字符串类型

- char(m) m取0～255
- varchar(m) m取0～65535，占值的长度+1个字节
- tinyblob   允许长度0～255字节，占值的长度+1个字节
- blob 允许长度0～65535字节，占值的长度+2个字节
- mediublob  允许长度0～167772150字节，占值的长度+3个字节
- longblob 允许长度0～2 **(*8\*4)字节，占值的长度+4个字节
- tinytext 允许长度0～255字节，占值的长度+2个字节
- text 允许长度0～255字节，占值的长度+2个字节
- mediumtext 允许长度0～255字节，占值的长度+3个字节
- longtext 允许长度0～255字节，占值的长度+4个字节
- varbinary(m)  占值的长度+1个字节
- binary(m)  占m长度的定长字节

```
其中char是定长的存储方式，长度不足会在结尾补空格。
varchar的存储会省略结尾的空格，然后记录省略空格的个数，所以长度会减去空格数，加上记录的1个值
```



### 4.枚举

优点:
1. 限制值
2. 节省空间
3. 运行效率高

```
field enmu('1','2','3'……) 
多选一
把这个字段需要的所有值枚举出来，那么在插入数据时，这个字段只能在这多个值中选一个。
```



### 5. 集合set

```
hobby set('吃','睡','玩','喝喝','抽',……)
多选多
把字段能选的值都列出来，在插入时能够在这多个值中选多个。
```



### 6.时间类型

- `date ` 4字节，年月日 例 1901/1/     可以以/ 或- 隔开
- `datetime`  8字节 年月日时分秒 例 1901/1/1 0:0:0   中间使用空格隔开
- `timestamp`  4字节 时间戳
- `time`  3字节 时分秒
- `year`  1字节 年



### 7.布尔型

- `bool值  ` 0和1 其中0是false，1是true



### 8.列(字段)的属性

- `null `和 `not null `默认是可以为空的。
- `default`   设置一个默认值。
- `primary key  `主键一般唯一，也可以设置联合主键。
- `auto_increment`  自增，默认从1开始，一定要与主键一起出现。
- `unique`  唯一，字段中值不可重复，是唯一的，一般是手机号，邮箱号，身份证号等
- `comment`  给自己看的注释， 不影响数据库。

### 注释

--单行注释

/\*多行注释*/

#单行注释 ，不建议使用，兼容差



## 运算符

```
select 123 + 543, 321 * 5, -456 / 2, 10 % 3, 2 / 0, 3 % 0;
/*
输出:
+-------------+---------+---------------+----------+-------+-------+
| 123 + 543 | 321 * 5 | -456 / 2         | 10 % 3 | 2 / 0  | 3 % 0 |
+-------------+---------+---------------+----------+-------+-------+
|		666		   |1605	 | -228.0000    |1 	     	  |NULL  |NULL |
+-------------+---------+---------------+----------+-------+-------+

1 row in set, 2 warnings (0.00 sec)
*/
```



#### 比较运算符 

用于判断

```
=      			 等于，不适用于null
<>或!=     不等于
<=>			  null安全的等于
<   	  	    小于
<=			  小于等于
>        		大于
>=			  大于等于
between    在范围中，中间
in  				在指定集合内，
is null			 是否为空
is not null	  是否非空
like 			    通配符匹配
regexp 或rlike   	正则表达式匹配

```



#### 逻辑运算符

not 或者 ！  非

and  或者 &&

or 或者 ||

xor  异或



## 查询语句select详解

`select` 既可以做查询, 也可以做输出

from 后面是数据源, 数据源可以写多个, 数据源一般是一个或多个表, 也可以是其他查询的结果。

```
select rand();		#随机生成一个0～1的数
select unix_timestamp();		#显示Unix时间戳
select id, name from student;		#用于查询
```



where  是做条件查询, 只返回结果为 True 的数据

```
select name from student where city = '上海';
```



group by分组

按照某一字段进行分组, 会把该字段中值相同的归为 一组, 将查询的结果分类显示, 方便统计。

如果有where 要放在 where 的后面 。

```
select sex, group_concat(name) from student where city='上海' group by sex;
```



having 

与where用法差不多，但是having能够使用聚合函数

having 出现在`group by`后面

```
select city, group_concat(birthday) from student group by city having
min(birthday) > '1995-1-1';
```



order by 按字段排序

排序分为升序 asc 降序 desc, 默认 asc (可以不不写)

order by 一般写在最后。

```
select * from student order by age desc;
```



limit  m，n

```
select 字段 from 表名 limit m, n;
-- 从第 m 行 开始,往下取 n 行 
select 字段 from 表名 limit m offset n;
-- 跳过前 n 行 , 取后 面的 m 行 
```



distinct 去重

```
select distinct city from student;
```



dual 虚拟表，只是为了语句的完整。

```
select now() from dual;
```



## 函数

### 聚合函数
|Name| Description|
| --------- | :--------------: |
| AVG()     | 返回参数的平均值 |
| BIT_AND() |   按位返回AND    |
| BIT_OR()  |    按位返回OR    |
| BIT_XOR() |   按位返回异或   |
|COUNT() 	|返回返回的行行行数|
|COUNT(DISTINCT) 	|返回许多不不同值的计数|
|GROUP_CONCAT() 	|返回连接的字符串串|
|JSON_ARRAYAGG() 	|将结果集作为单个JSON数组返回|
|JSON_OBJECTAGG() 	|将结果集作为单个JSON对象返回|
|MAX() 	|返回最大大值|
|MIN() |	返回最小小值|
|STD() 	|返回样本的标准差|
|STDDEV() 	|返回样本的标准差|
|STDDEV_POP() 	|返回样本的标准差|
|STDDEV_SAMP() 	|返回样本标准差|
|SUM() 	|归还总和|
|VAR_POP() 	|返回样本的标准差异|
|VAR_SAMP() 	|返回样本方方差|
|VARIANCE() 	| 返回样本的标准差异|





### 数值计算类函数

![1567601582583](/home/qx/.config/Typora/typora-user-images/1567601582583.png)



### 日期计算类函数

![1567601614111](/home/qx/.config/Typora/typora-user-images/1567601614111.png)



### 字符串相关函数

![1567601675267](/home/qx/.config/Typora/typora-user-images/1567601675267.png)



### 其他函数

![1567601689295](/home/qx/.config/Typora/typora-user-images/1567601689295.png)



## 多表查询

#### union 联合查询

UNION 操作符用用于合并两个或多个 SELECT 语句句的结果集。
union要求:

1. 两边 select 语句句的字段数必须一样
2. 两边可以具有不不同数据类型的字段

3. 字段名默认按照左边的表来设置

```
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```



#### 内连接 inner join

INNER JOIN 关键字在表中存在至少一个匹配时返回行。

连接在使用的时候on条件越准确越好。

```mysql
SELECT 字段
FROM 表1 INNER JOIN 表2
ON 表1.字段=表2.字段;
-- 或:
SELECT column_name(s)
FROM table1 JOIN table2
ON table1.column_name=table2.column_name;
```



左连接 left join

LEFT JOIN 关键字从左表(table1)返回所有的行,即使右表(table2)中没有匹配。如果右表中没有匹配,则结果为 NULL。

```mysql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name=table2.column_name;
-- 或:
SELECT column_name(s)
FROM table1
LEFT OUTER JOIN table2
ON table1.column_name=table2.column_name;
```



右连接 right join

与左连接一样

```
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name=table2.column_name;
-- 或:
SELECT column_name(s)
FROM table1
LEFT OUTER JOIN table2
ON table1.column_name=table2.column_name;
```



#### 子查询
查询的语句中还嵌套有一个查询
`select name from student where id in (select id from score where math > 10);`



## 权限操作

1. 只授予能满足需要的最小权限,防止用户执行危险操作。
2. 限制用户的登录主机,防止不速之客登录数据库。
3. 禁止或删除没有密码的用用户。
4. 禁止用户使用弱密码。
5. 定期清理无效的用户,回收权限或者删除用户。

mysql由于版本的更新，权限的操作有了不同的方式。

##### 8.0 版本之前权限操作

```mysql
GRANT ALL PRIVILEGES on *.* to '用户名'@'主机' IDENTIFIED BY "密码" WITH
GRANT OPTION;
-- 其中 all privileges 表示所有权限
--  *.*         *表示所有，点前面的*表示数据库，点后面的*表示表，
-- 用户名就是用户名，主机是一个地址，一般自己使用localhost,表示本机
-- with grant option 表示拥有再次授权权限
flush privileges; -- 刷新使权限生生效
```

##### 8.0 之后增加的操作

```mysql
CREATE USER `用用户名`@`主机` IDENTIFIED BY '密码';
-- 创建账户
GRANT ALL ON *.* TO `用用户名`@`主机` WITH GRANT OPTION;
-- 授权

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '你的密码';
-- 修改秘密 

show grants;
-- 查看当前用户的权限
show grants for 'abc'@'localhost';
-- 查看用户 abc 的权限

revoke delete on *.* from 'abc'@'localhost';
--回收权限

use mysql;  -- 打开（使用）mysql数据库
select host, user from user; -- 查询用户相关信息
drop user 用户名@'%';   -- 删除用户
```





### 视图

试图是为了更便利得显示查询结果而产生的虚拟表。其本质上就是一个查询结果。

试图的定义简化了多次查询该数据的语句。

一般视图表的名称以 v_ 为前缀, 用来与正常表进 行区分。

````mysql
-- 创建视图语句
create view v_ues as 
select *from student;
 -- 为查询student表得到的结果创建一个视图。
 -- 视图只为查询简单化，对人友好，对计算机不算友好
````



## 存储引擎

存储引擎就是如何存储数据、如何为数据建立索引和如何更新、查询数据等技术的实现方法。
MySQL 默认支持多种存储引擎,以适用于不同领域 的数据库应用需要,用户可以通过选择使用不同的
存储引擎提高应用的效率,提供灵活的存储。

```mysql
show variables like '%storage_engine';
-- 模糊查找
show engines;
-- 查看引擎
```

### mysql中的存储引擎(表使用最多的还是myisam和innodb)

![1567676676920](/home/qx/.config/Typora/typora-user-images/1567676676920.png)



### 引擎的存储方方式

##### myisam

myisam将一一张表存储为三个文文件
demo.frm -> 表的结构
demo.MYD -> 存储的是数据
demo.MYI -> 存储的是表的索引

##### innodb

innodb将一一张表存储为两个文文件
demo.frm -> 表的结构+表的索引
demo.ibd -> 存储的是数据
ibd存储是有限的, 存储不不足足自自动创建ibd1, ibd2



### 存储引擎特性

InnoDB
		事务型数据库的首选引擎,支持事务安全表(ACID),支持行锁定和外键,InnoDB是默认的
MySQL引擎。
InnoDB主要特性有:

1. InnoDB 给 MySQL 提供了了具有提交、回滚、崩溃恢复能力的事物安全存储引擎。
2. InnoDB 是为处理巨大数据量的最大性能设计。它的 CPU 效率比比其他基于磁盘的关系型数据
    库引擎高。
3. InnoDB 存储引擎自带缓冲池,可以将数据和索引缓存在内存中。
4. InnoDB 支持外键完整性约束。
5. InnoDB 被用在众多需要高性能的大型数据库站点上
6. InnoDB 支持行级锁



MyISAM
		MyISAM 基于 ISAM 存储引擎,并对其进行扩展。它是在Web、数据仓储和其他应用环境下最常使
用的存储引擎之一。MyISAM 拥有较高的插入、查询速度,但不支持事物。
MyISAM主要特性有:

1. 大文件支持更好
2. 当删除、更新、插入混用时,产生更少碎片。
3. 每个 MyISAM 表最大索引数是64,这可以通过重新编译来改变。每个索引最大的列数是16
4. 最大的键长度是1000字节。
5. BLOB和TEXT列可以被索引
6. NULL 被允许在索引的列中,这个值占每个键的0~1个字节
7. 所有数字键值以高字节优先被存储以允许一个更高的索引压缩
8. MyISAM 类型表的 AUTO_INCREMENT 列更新比比 InnoDB 类型的 AUTO_INCREMENT 更更快
9. 可以把数据文件和索引文件放在不同目目录
10. 每个字符列可以有不同的字符集
11. 有 VARCHAR 的表可以固定或动态记录长度
12. VARCHAR 和 CHAR 列可以多达 64KB
13. 只支持表锁

MEMORY
		MEMORY 存储引擎将表中的数据存储到内存中,为查询和引用其他表数据提供快速访问。



```mysql
create table `tablename` (……
)engine=myisam charset=uft8;
-- 建表指定引擎
alter table `tablename` engine=innodb;
-- 改引擎
```



## 索引

添加索引可以加快查找速度。

索引的优点:
一个字:快!使用索引能极大提升查询速度。
索引的缺点:

1. 额外的使用了一些存储的空间
2. 索引会让写的操作变慢



#### 索引的创建原则

1. 适合用于频繁查找的列
2. 适合经常用于条件判断的列
3. 适合经常由于排序的列
4. 不适合数据不多的列
5. 不适合很少查询的列



```mysql
create table 表(
id int not null,
username varchar(16) not null,
index 索引名(字段名(长度))
);
-- 创建表时添加索引，这里长度是索引的长度，与原字段数据类型长度无关。

create unique index 索引名 on 表(字段名(⻓长度));
-- 或
create table 表(
id int not null,
username varchar(16) not null,
unique 索引名 (字段名(⻓长度))
);
-- 创建唯一索引，唯一索引的值必须是唯一的，即字段内数据不重复。

create index `索引名` on 表名(字段名(长度));
-- 为已有的表中字段添加索引

drop index [索引名] on 表;
-- 删除索引

show index from table_name; 
-- 查看索引
```



## 关系数据库中的关系

#### 一对一

在 A 表中有一条记录,在 B 表中同样有唯一条记录相匹配
比如: 学生表和成绩表

#### 一对多或多对以

在 A 表中有一条记录,在 B 表中有多条记录一直对应
比如: 一个学生有多门课的成绩

#### 多对多

A 表中的一条记录有多条 B 表数据对应, 同样 B 表中一条数据在 A 表中也有多条与之对应
比如: 商品对应客户



## 外键foreign

外键可以确保关系数据的完整性，但是会降低效率。

```mysql
alter table `order` add constraint `fk_prod_id` foreign key (`pid`) references `product`(`id`);
-- 其中 order是外键所在的表名，fk_prod_id是外键的名字 pid是外键字段，product(id)是被绑定表(字段)。

```

有外键的字段在删除数据时，先删除外键对应的数据，不然会报错。



## 数据库事务、锁、存储过程、pycharm连接数据和数据备份与恢复







### 事务

事务主要用用于处理理操作量大、复杂度高、并且关联性强的数据。
比如说, 在人员管理理系统中, 你删除一个人员, 你即需要删除人员的基本资料, 也要删除和该人员相关的信息, 如信箱, 文章等, 这样, 这些数据库操作语句句就构成一个事务!
在 MySQL 中只有 Innodb 存储引擎支持事务。
事务处理可以用来维护数据库的完整性, 保证成批的 SQL 语句要么全部执行, 要么全部不执行。主要针对insert, update, delete 语句而设置

#### 事务四大特性

1. 原子性 (Atomicity) :
   事务中的所有操作, 要么全部完成, 要么全部不完成, 不会结束在中间某个环节。
   事务在执行过程中发生错误, 会被回滚 (Rollback) 到事务开始前的状态, 就像这个事务从来没有执行过一样。

2. 一致性 (Consistency):
   在事务开始之前和事务结束以后, 数据库的完整性没有被破坏。
   这表示写入的资料必须完全符合所有的预设规则, 这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。

3. 隔离性 (Isolation):
   数据库允许多个并发事务同时对其数据进行读写和修改的能力, 隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。

   事务隔离分为不不同级别, 包括:

   ​	读取未提交 (Read uncommitted)

   ​	读提交 (read committed)

   ​	可重复读 (repeatable read)

   ​	串行化 (Serializable)

   

4. 持久性 (Durability):
   事务处理理结束后, 对数据的修改就是永久的, 即便便系统故障也不不会丢失。

#### 语法与使用

开启事务:` BEGIN 或 START TRANSACTION`
提交事务: `COMMIT `, 提交会让所有修改生效
回滚: `ROLLBACK` , 撤销正在进行的所有未提交的修改
创建保存点: `SAVEPOINT identifier`
删除保存点:` RELEASE SAVEPOINT identifier`
把事务回滚到保存点: `ROLLBACK TO identifier`
设置事务的隔离级别: `ET TRANSACTION`
InnoDB 提供的隔离级别有
`READ
UNCOMMITTED
READ COMMITTED
REPEATABLE READ
SERIALIZABLE`



例子：

```mysql
create table `abc` (
id int unsigned primary key auto_increment,
name varchar(32) unique,
age int unsigned) charset=utf8;
begin;
insert into abc (name, age) values ('aa', 11);
insert into abc (name, age) values ('bb', 22);
-- 在事务中查看一下数据
-- 同时另开一个窗口口,连接到 MySQL 查看一下数据是否一样
select * from abc;
commit;
begin;
insert into abc (name, age) values ('cc', 33);
insert into abc (name, age) values ('dd', 44);
update abc set age=77 where name='aa';
-- 在事务中查看一下数据
select * from abc;
rollback;
select * from abc;
-- 事务结束后在查看一下数据
```









```mysql
create table `abc` (
id int unsigned primary key auto_increment,
name varchar(32) unique,
age int unsigned) charset=utf8;
begin;
insert into abc (name, age) values ('aa', 11);
insert into abc (name, age) values ('bb', 22);
-- 在事务中查看一下数据
-- 同时另开一个窗口,连接到 MySQL 查看一一下数据是否一样
select * from abc;
commit;
begin;
insert into abc (name, age) values ('cc', 33);
insert into abc (name, age) values ('dd', 44);
update abc set age=77 where name='aa';
-- 在事务中查看一下数据
select * from abc;
rollback;
select * from abc;
-- 事务结束后在查看一下数据
```



### 🔓锁

锁是计算机协调多个进程或线程并发访问某一资源的机制。
锁保证数据并发访问的一致性、有效性;
锁冲突也是影响数据库并发访问性能的一个重要因素。
锁是Mysql在服务器层和存储引擎层的的并发控制。



##### 行级锁
行级锁是Mysql中锁定粒度最细的一一种锁,表示只针对当前操作的行进行加锁。
行级锁只有 InnoDB 引擎支支持。
行级锁能大大减少数据库操作的冲突。其加锁粒度最小,但加锁的开销也最大。
特点:开销大,加锁慢;会出现死锁;锁定粒度最小,发生锁冲突的概率最低,并发度也最
高高。
##### 表级锁
表级锁是MySQL中锁定粒度最大的一种锁
对当前操作的整张表加锁,它实现简单,资源消耗较少,被大部分MySQL引擎支持。
特点:开销小,加锁快;不会出现死锁;锁定粒度大,发出锁冲突的概率最高,并发度最低。

##### 共享锁 (读锁)
其他用户可以并发读取数据,但任何事务都不不能对数据进行修改,直到已释放所有共享锁。
##### 排他锁 (写锁)
如果事务 T 对数据 A 加上排他锁后,则其他事务不不能再对 A 加任何类型的封锁。持有排他锁的事务既能读数据,又又能修改数据。
##### 乐观锁(Optimistic Lock)
假设不不会发生并发冲突,只在提交操作时检查是否违反数据完整性。 乐观锁不能解决脏读的问题。

乐观锁, 顾名思义,就是很乐观,每次去拿数据的时候都认为别人不会修改,所以不会上锁,但是在更新的时候会判断一下在此期间别人有没有去更新这个数据,可以使用版本号等机制。乐观锁适用于多读的应用用类型,这样可以提高吞吐量,像数据库如果提供类似于write_condition机制的其实都是提供的乐观锁。

##### 悲观锁(Pessimistic Lock)

假定会发生并发冲突,屏蔽一一切可能违反数据完整性的操作。
悲观锁,顾名思义,就是很悲观,每次去拿数据的时候都认为别人人会修改,所以每次在拿数据的时
候都会上锁,这样别人想拿这个数据就会block直到它拿到锁。传统的关系型数据库里边就用用到了
很多这种锁机制,比比如行锁,表锁等,读锁,写锁等,都是在做操作之前先上锁。













#### 存储过程

存储过程(Stored Procedure)是一种在数据库中存储复杂程序,以便外部程序调用的一种数据 库对象。
存储过程是为了完成特定功能的SQL语句句集,经编译创建并保存在数据库中,用户可通过指定存储过程的名字并给定参数(需要时)来调用用执行。
存储过程思想上很简单,就是数据库 SQL 语言层面的代码封装与重用。

1. 优点
存储过程可封装,并隐藏复杂的商业逻辑。
存储过程可以回传值,并可以接受参数。
存储过程无法使用 SELECT 指令来运行,因为它是子程序,与查看表,数据表或用户定义函数不同。
存储过程可以用在数据检验,强制实行商业逻辑等。
2. 缺点
存储过程,往定制化于特定的数据库上,因为支持的编程语言不同。当切换到其他厂商的数据库系统时,需要重写原有的存储过程。
存储过程的性能调校与撰写,受限于各种数据库系统。

```mysql
delimiter //
-- 定义前,将分隔符从；改成 //
create procedure foo(in uid int)
#in是关键字 ，uid是参数，int是数据类型
begin
select * from student where `id`=uid;
update student set `city`='北京' where `id`=uid;
end//
delimiter;

call foo(3);
```





延伸阅读
https://www.zhihu.com/question/19749126
https://segmentfault.com/q/1010000004907411



#### pycharm连接数据库

需要安装第三方库  pip install pymysql

在使用前导入即可

```python
import pymysql
db = pymysql.connect(host='localhost',
						user='user',
						password='passwd',
						db='db',
						charset='utf8')
	# host表示数据库地址，user是数据库用户，db表示使用的数据库名
try:
	with db.cursor() as cursor:
																																	# 插入
		sql = "INSERT INTO `users` (`email`, `password`) VALUES (%s, %s)"
		cursor.execute(sql, ('webmaster@python.org', 'very-secret'))
													# 需要手动提交才会执行
	db.commit()
	with db.cursor() as cursor:
						# 读取记录
		sql = "SELECT `id`, `password` FROM `users` WHERE `email`=%s"
		cursor.execute(sql, ('webmaster@python.org',))
		result = cursor.fetchone()
		print(result)
finally:
	db.close()

```



#### 数据备份和恢复

```
mysqldump -h localhost -u root -p123456 dbname > dbname.sql
-- 备份数据库中的所有数据

mysql -h localhost -u root -p123456 dbname < ./dbname.sql
-- 恢复数据入dbname中
```











