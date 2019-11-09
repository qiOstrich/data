# SQL

主从复制

```python
# 10.11.55.134
```

binlog机制(二进制日志传输)

从服务器连接主服务器(从服务器中有主服务器的帐号和密码还有host和port)

当主服务器得知某一个从服务器连接的时候(当用户对主服务器写入一组数据的时候)

主服务器会产生一组日志(日志中包含的是用户的行为,操作某库某表,数据内容的id)

主服务器把binlog文件传输给从服务器

把数据拷贝到从服务器

### 主服务器配置

```python
/etc/my.cnf
###################主机########################
log-bin=mysql-bin      
server-id = 101170101
#master
binlog-do-db=库名     #只同步某一个数据库
binlog-ignore-db=mysql    #避免同步mysql库
##############################################

service mysqld restart

show msater status\G
```

### 从服务器配置

```python
/etc/my.cnf
###################从机########################
log-bin=mysql-bin      
server-id = 101170101
#slave
replicate-do-db= python       #只复制某一个库
replicate-ignore-db=mysql    #避免复制到mysql库
##############################################
service mysqld restart
```

```python
#mysql -uxxxxx -pxxxxx
stop slave;

change master to
master_host='10.11.55.134',   #主服务器的host
master_user='hal',                       #主服务器的用户名
master_password='123456',   
master_log_file='mysql-bin.000046',   #主服务器的binlog文件名
master_log_pos=154;                                  #主服务器对接文件编号

start slave;

show slave status\G

'''
Slave_IO_Running: Yes
Slave_SQL_Running: Yes
'''
```











