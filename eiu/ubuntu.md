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

### 当你使用一台新ubuntu机器时 ###

#### 密钥login, 不允许密码login ####

```bash
ubuntu@utuntu:~$ vi ~/.ssh/authorized_keys 
ubuntu@utuntu:~$ ls ~/.ssh/authorized_keys 
ubuntu@utuntu:~$ sudo vi /etc/ssh/sshd_config 
ubuntu@utuntu:~$ grep PasswordAu -rn /etc/ssh/sshd_config 
124:PasswordAuthentication no 
ubuntu@utuntu:~$ sudo systemctl restart sshd
ubuntu@utuntu:~$ sudo systemctl status sshd
ubuntu@utuntu:~$ 
```

#### firewall ####

```bash
ubuntu@utuntu:~$ sudo ufw allow 22
ubuntu@utuntu:~$ sudo ufw allow 2376
ubuntu@utuntu:~$ sudo ufw enable
ubuntu@utuntu:~$ sudo ufw status
```

如果要删除规则, 先要查到规则number, 然后 delete. 
**每删除一条,要再次查询,再删除下一条规则**

```bash
sudo ufw status numbered
sudo ufw delete $number
```

#### network ####

设置固定IP

##### 如果是 ubuntu 18 #####

参考
https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux

#### apt ####

https://blog.csdn.net/zhangjiahao14/article/details/80554616
https://blog.csdn.net/xiangxianghehe/article/details/80112149

#### docker ####

https://docs.docker.com/install/linux/docker-ce/ubuntu/
https://eiu.app/post/add-user-to-docker-group/
https://eiu.app/cheatsheets/eiu/docker

##### 安装完成后,配置docker daemon #####

```bash
ubuntu@utuntu:~$ sudo vi /etc/docker/daemon.json
ubuntu@utuntu:~$ cat /etc/docker/daemon.json 
{                                                               
	"hosts": ["tcp://0.0.0.0:2376","unix:///var/run/docker.sock"],
	"registry-mirrors": ["https://0*****y.mirror.aliyuncs.com"]  
}                                                               
ubuntu@utuntu:~$ 
ubuntu@utuntu:~$ sudo systemctl status docker
● docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
ubuntu@utuntu:~$ sudo vi /lib/systemd/system/docker.service 
ubuntu@utuntu:~$ sudo systemctl daemon-reload 
ubuntu@utuntu:~$ sudo systemctl restart docker 
ubuntu@utuntu:~$ sudo systemctl status docker 
ubuntu@utuntu:~$ netstat -tlnp | grep 2376
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp6       0      0 :::2376                 :::*                    LISTEN      -                   
ubuntu@utuntu:~$
```

##### (可选, 视情况)统一配置container dns

```bash
ubuntu@utuntu:~$ cat /etc/docker/daemon.json 
{                                                               
	"hosts": ["tcp://0.0.0.0:2376","unix:///var/run/docker.sock"],
	"registry-mirrors": ["https://0d6wdn2y.mirror.aliyuncs.com"],
	"dns" : ["192.168.168.222"]
}                                                               
ubuntu@utuntu:~$ sudo systemctl restart docker
```

##### docker与ufw配合

https://blog.36web.rocks/2016/07/08/docker-behind-ufw.html

或者出了问题, 参考一下 http://github.com/eiuapp/linux-handbook

### ubuntu之设置时区和在线同步时间 ###

https://blog.csdn.net/w786572258/article/details/51248053

#### 修改时区 ####

Linux默认情况下使用UTC格式作为标准时间格式，如果在Linux下运行程序，且在程序中指定了与系统不一样的时区的时候，可能会造成时间错误。如果是Ubuntu的桌面版，则可以直接在图形模式下修改时区信息，但如果是在Server版呢，则需要通过tzconfig来修改时区信息了。使用方式(如将时区设置成Asia/Chongqing)：
 
```bash
sudo tzconfig  
```

如果命令不存在请使用:

```bash
dpkg-reconfigure tzdata
```

然后按照提示选择 Asia对应的序号，选完后会显示一堆新的提示输入城市名，如Shanghai或Chongqing，最后再用 sudo date -s “” 来修改本地时间。
按照提示进行选择时区，然后：

```bash
sudo cp /usr/share/zoneinfo/Asia/Chongqing /etc/localtime
```

上面的命令是防止系统重启后时区改变。

#### 网上同步时间 ####

```
1.安装ntpdate工具
# sudo apt-get install ntpdate
2.设置系统时间与网络时间同步
# ntpdate cn.pool.ntp.org
3.将系统时间写入硬件时间
# hwclock -w
```
 
这里公布2个NTP服务器地址:
```
cn.pool.ntp.org
ntp.api.bz
```
## ref
- https://blog.csdn.net/zhongdajiajiao/article/details/52189793
