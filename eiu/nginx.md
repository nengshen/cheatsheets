---
title: nginx
category: nginx
layout: 2017/sheet
---


## install

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
