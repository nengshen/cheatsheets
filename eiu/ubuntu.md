---
title: ubuntu
category: ubuntu
layout: 2017/sheet
---

## 常用命令

### ubuntu查看已安装所有软件包

```bash
dpkg -l ## --列出当前系统中所有的包.可以和参数less一起使用在分屏查看. (类似于rpm -qa)
dpkg -l |grep -i "软件包名" ## --查看系统中与"软件包名"相关联的包.
```

```
期望状态=未知(u)/安装(i)/删除(r)/清除(p)/保持(h)
| 状态=未安装(n)/已安装(i)/仅存配置(c)/仅解压缩(U)/配置失败(F)/不完全安装(H)/触发器等待(W)/触发器未决(T)
|/ 错误?=(无)/须重装(R) (状态，错误：大写=故障)
||/ 名称                             版本                                       体系结构：   描述
--------------------- 
```

- https://blog.csdn.net/ly890700/article/details/75042785

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
