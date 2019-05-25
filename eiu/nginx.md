---
title: nginx
category: nginx
layout: 2017/sheet
---


## install

### 编译常见错误

#### SSL modules require the OpenSSL library
```bash
./configure: error: SSL modules require the OpenSSL library. 
```
https://blog.csdn.net/t1anyuan/article/details/

解决方法: 
Centos需要安装openssl-devel 
Ubuntu则需要安装:libssl-dev

```bash
sudo apt-get install libssl-dev
```


#### the HTTP rewrite module requires the PCRE library

https://www.cnblogs.com/tinywan/p/6377066.html

```bash
sudo apt-get install libpcre3 libpcre3-dev
```

#### ./configure: error: the HTTP gzip module requires the zlib library.

https://www.cnblogs.com/tinywan/p/6377066.html

```bash
sudo apt-get install zlib1g-dev
```


### with solaris

#### 编译

https://www.nginx.com/resources/wiki/start/topics/tutorials/solaris_10_u5/

https://www.nginx.com/resources/wiki/start/topics/tutorials/solaris_11/


#### 不编译

https://www.opencsw.org/packages/CSWnginx/


```bash
pkgadd -d http://get.opencsw.org/now
/opt/csw/bin/pkgutil -U
/opt/csw/bin/pkgutil -i nginx 
/opt/csw/bin/pkgutil -y -i nginx 
/usr/sbin/pkgchk -L CSWnginx # list files
```

/opt/csw/bin/pkgutil -i nginx 是为了查看版本号，看是不是我们想要的版本，如果不是，则不安装。


## ref
- https://www.nginx.com/resources/wiki/start/topics/tutorials/solaris_10_u5/
