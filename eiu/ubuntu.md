---
title: ubuntu
category: ubuntu
layout: 2017/sheet
---

## 常用命令

### ubuntu 修改 ssh默认端口号

Linux中SSH默认端口为22，为了安全考虑，我们有必要对22端口进行修改，现修改端口为60000；

修改方法如下：
在/etc/ssh/sshd_config中找到Port 22，将其修改为60000,或使用/usr/sbin/sshd -p 60000指定端口。

如果用户想让22和60000端口同时开放，只需在/etc/ssh/sshd_config增加一行内容如下：

```bash
[root@localhost /]# vi /etc/ssh/sshd_config
Port 22
Port 60000
```

保存并退出

```bash
[root@localhost /]#service ssh restart
```

## ref
- https://blog.csdn.net/zhongdajiajiao/article/details/52189793
