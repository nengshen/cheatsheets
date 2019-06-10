---
title: mysql
category: mysql
layout: 2017/sheet
---

### 时间

#### 建表sql 使用 current_timestamp 代替 NULL

```
  `create_date` timestamp NULL DEFAULT NULL COMMENT '创建时间',
  `update_date` timestamp NULL DEFAULT NULL COMMENT '更新时间',
```

修改成
  
```
  `create_date` timestamp NULL DEFAULT current_timestamp() COMMENT '创建时间',
  `update_date` timestamp NULL DEFAULT NULL ON UPDATE current_timestamp() COMMENT '更新时间',
```

### 不登陆数据库执行 MySQL 命令

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


### Navicat for Mysql 连接阿里云数据库

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
