---
title: solaris
category: solaris
layout: 2017/sheet
---

## 常用命令

```bash
svcs -a # 確認一下相關的服務的狀態  查看所有服务
inetadm | grep -i # 查看服务
svcadm disable svc:  # 关闭服务

```



### inetadm

To enable a disabled rsh/rlogin service, type the following command:
```
# inetadm -e rlogin
```
To disable an enabled rsh/rlogin service, type the following command:
```
# inetadm -d rlogin
```

### 禁用 rlogin

```bash
-bash-3.2# svcs -a | grep rlogin
online         2017     svc:/network/login:rlogin
-bash-3.2# svcadm disable rlogin
-bash-3.2# svcadm disable svc:/network/login:rlogin
-bash-3.2# svcs -a | grep rlogin
disabled       13:52:41 svc:/network/login:rlogin
-bash-3.2# 
```


### 禁用 X Font Service (XFS)

```bash
-bash-3.2# svcs -a | grep xfs   
online         2017     svc:/application/x11/xfs:default
-bash-3.2# svcadm disable svc:/application/x11/xfs:default
-bash-3.2# svcs -a | grep xfs
disabled       14:04:46 svc:/application/x11/xfs:default
-bash-3.2# 
```

### (未测试)禁用 rsh出访 服务

http://sort.symantec.com/public/documents/sfha/6.0.1/solaris/productguides/html/virtualstore_install/apes04.htm

```bash
-bash-3.2# svcadm disable svc:/network/shell:default
-bash-3.2# svcs -a | grep rsh
-bash-3.2# inetadm | grep -i rsh  
-bash-3.2# 
```




## ref
- https://blog.csdn.net/upcorange/article/details/8266170
- http://sort.symantec.com/public/documents/sfha/6.0.1/solaris/productguides/html/virtualstore_install/apes04.htm
- https://www.twblogs.net/a/5b8a4fa52b71775d1ce65e49
