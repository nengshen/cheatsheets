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



### Nginx 做代理时浏览器报错 net::ERR_CONTENT_LENGTH_MISMATCH

https://github.com/xhlwill/blog/issues/17
https://stackoverflow.com/questions/25993826/err-content-length-mismatch-on-nginx-and-proxy-on-chrome-when-loading-large-file

这个问题, 我一度誤认为是对静态文件要特别处理呢.

```
server {
        listen 8082;
        server_name 192.168.168.137 www.szeciss.com;
        location / {
         #    proxy_pass http://127.0.0.1:3021/;
              proxy_pass http://lvchuang-admin-server;
              proxy_set_header Host $host;
              proxy_set_header X-Real-IP $remote_addr;
              proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
              }

        location ~ .*\.(gif|jpg|jpeg|bmp|png|ico|txt|js|css)$ {
                root /home/ubuntu/lcnx/local/build/;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header Host $http_host;
        }
}
```
经过上面的修改后,则縮减至

```
server {
        listen 8082;
        server_name 192.168.168.137 www.szeciss.com;
        location / {
         #    proxy_pass http://127.0.0.1:3021/;
              proxy_pass http://lvchuang-admin-server;
              proxy_set_header Host $host;
              proxy_set_header X-Real-IP $remote_addr;
              proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
              }
}
```
## ref
- https://www.nginx.com/resources/wiki/start/topics/tutorials/solaris_10_u5/
