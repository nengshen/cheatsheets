---
title: vagrant
category: vagrant
layout: 2017/sheet
---

## Vagrant 常用命令清单

* vagrant box add 添加box
* vagrant init 初始化 box
* vagrant up 启动虚拟机
* vagrant ssh 登录虚拟机
* vagrant box list 列出 Vagrant 当前 box 列表
* vagrant box remove 删除相应的 box
* vagrant destroy 停止当前正在运行的虚拟机并销毁所有创建的资源
* vagrant halt 关机
* vagrant package 把当前的运行的虚拟机环境进行打包为 box 文件
* vagrant plugin 安装卸载插件
* vagrant reload 重新启动虚拟机，重新载入配置文件
* vagrant resume 恢复被挂起的状态
* vagrant status 获取当前虚拟机的状态
* vagrant suspend 挂起当前的虚拟机
* vagrant global-status 查看当前 vagrant 管理的所有 vm 信息
* vagrant ssh-config 输出用于 ssh 连接的一些信息

### 通过 ssh 登录 vagrant box ###

```
vagrant ssh-config
ssh vagrant@127.0.0.1 -p 2222 -i D:/vag-files/ubuntu16/.vagrant/machines/default/virtualbox/private_key
```

### Vagrant 手册之 Vagrantfile - SSH 设置 config.ssh

https://blog.csdn.net/kikajack/article/details/80148045



## ref
- https://blog.csdn.net/qianghaohao/article/details/80038096
