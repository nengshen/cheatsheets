---
title: mysql
category: mysql
layout: 2017/sheet
---

### timestamp时间 ###

#### 建表sql 使用 current_timestamp 代替 NULL ####

```
  `create_date` timestamp NULL DEFAULT NULL COMMENT '创建时间',
  `update_date` timestamp NULL DEFAULT NULL COMMENT '更新时间',
```

修改成
  
```
  `create_date` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_date` timestamp NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
```

或者 

```
  `create_date` timestamp NULL DEFAULT current_timestamp() COMMENT '创建时间',
  `update_date` timestamp NULL DEFAULT NULL ON UPDATE current_timestamp() COMMENT '更新时间',
```

可以直接执行mysql命令

```
ALTER TABLE tableName MODIFY create_date timestamp NOT NULL DEFAULT current_timestamp() COMMENT '创建时间';
ALTER TABLE tableName MODIFY update_date timestamp NULL DEFAULT NULL ON UPDATE current_timestamp() COMMENT '更新时间';
```

如果要批量修改, 则想办法构造上面2语句就可以了.

在mysql下执行, `show tables;`得到所有表名.

### 不登陆数据库执行 MySQL 命令 ###

有的时候需要查看数据库的某些信息，然后继续接下来的 shell 命令操作，登录数据库在退出嫌麻烦可以使用这招：

例 1：列出所有数据库

```bash
mysql -h host_name -P3306 -u user_name -p'password' -se "show databases;"
```

例 2：列出 database 下的所有表

```bash
mysql -h host_name -P3306 -u user_name -p'password' -D database -se "show tables;"
```

- host_name： 数据库 host 或者 IP 地址；
- user_name： 登录数据库用户名；
- password：登录数据库密码；
- database: 数据库名;


### mysql create database 时要使用utf8mb4 ###


```bash
CREATE DATABASE IF NOT EXISTS lcnx_20190512 CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

https://blog.csdn.net/kikajack/article/details/84668924
http://seanlook.com/2016/10/23/mysql-utf8mb4/


### Navicat for Mysql 连接阿里云数据库 ###

https://blog.csdn.net/wk2197727/article/details/51822352


### mysql 替换函数replace()实现mysql替换指定字段中的字符串

https://blog.csdn.net/qq_36663951/article/details/78791138

mysql 替换字符串的实现方法:

mysql中replace函数直接替换mysql数据库中某字段中的特定字符串，不再需要自己写函数去替换，用起来非常的方便。 mysql 替换函数replace()
 
```
UPDATE `table_name` SET `field_name` = replace (`field_name`,'from_str','to_str') WHERE `field_name` LIKE '%from_str%'
```
说明：
- table_name  表的名字
- field_name  字段名
- from_str  需要替换的字符串
- to_str  替换成的字符串

例如：

```
mysql> SELECT REPLACE('www.lvtao.net', 'www', 'http://www');
```
-> 'https://www.lvtao.net'

该函数是多字节安全的,也就是说你不用考虑是中文字符还是英文字符.


### mysqldump


```bash
lcnx@iZwz95dxhc92qtibd4f399Z:~/backup/mysql$ cat backup-mysql.sh 
#!/bin/bash

echo "`date`"
echo `date '+%Y%m%d%H%M%S'`
now=`date '+%Y%m%d%H%M%S'`

mysqldump -h "*****" -u***** -p'*****' --database lcnx_20190512 > /home/lcnx/backup/mysql/mysql-lcnx_20190512-${now}.sql
docker exec -it  mysql03-20190525 mysqldump -uroot -p123456 lcnx_20190512 > ${HOME}/backup/mysql/mysql-lcnx_20190512-${now}.sql

echo "mysqldump done."

```

### mysql密码中有特殊字符&在命令行下登录

https://blog.csdn.net/feinifi/article/details/80265916

用单引号

### mysql UTC timezone ###

https://www.cnblogs.com/shiqiangqiang/p/8393662.html

```bash
ubuntu@utuntu:~/lcnx/local/lvchuang-admin-server$ docker exec -it mysql03-20190525 bash
root@086bdb8baa32:/# mysql -uroot -p123456 -e "show variables like \"%time_zone%\";"
Warning: Using a password on the command line interface can be insecure.
+------------------|--------+
| Variable_name    | Value  |
+------------------|--------+
| system_time_zone | UTC    |
| time_zone        | +08:00 |
+------------------|--------+
root@086bdb8baa32:/# mysql -uroot -p123456 -e "select curtime();"
Warning: Using a password on the command line interface can be insecure.
+-----------+
| curtime() |
+-----------+
| 14:31:24  |
+-----------+
root@086bdb8baa32:/# 

```

以下记录修改mysql时区的几种方法。

具体：

#### 方法一：通过mysql命令行模式下动态修改 ####

1.1 查看mysql当前时间，当前时区

```
> select curtime();   #或select now()也可以
+-----------+
| curtime() |
+-----------+
| 15:18:10  |
+-----------+

> show variables like "%time_zone%";
+------------------|--------+
| Variable_name    | Value  |
+------------------|--------+
| system_time_zone | CST    |
| time_zone        | SYSTEM |
+------------------|--------+
2 rows in set (0.00 sec)
```
#time_zone说明mysql使用system的时区，system_time_zone说明system使用CST时区
 
1.2 修改时区

```
> set global time_zone = '+8:00';  ##修改mysql全局时区为北京时间，即我们所在的东8区
> set time_zone = '+8:00';  ##修改当前会话时区
> flush privileges;  #立即生效
```
 
#### 方法二：通过修改my.cnf配置文件来修改时区 ####


`vim /etc/my.cnf`  在[mysqld]区域中加上

```
default-time_zone = '+8:00'
```

```
/etc/init.d/mysqld restart  ##重启mysql使新时区生效
```

#### 方法三：如果不方便重启mysql，又想临时解决时区问题，可以通过php或其他语言在初始化mysql时初始化mysql时区 ####

这里，以php为例，在mysql_connect()下使用mysql_query(“SET time_zone = ‘+8:00′”)。
这样可以在保证你不重启的情况下改变时区。但是mysql的某些系统函数还是不能用如：now()。这句，还是不能理解。

