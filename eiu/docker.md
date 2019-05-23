---
title: docker-compose
category: Devops
layout: 2017/sheet
prism_languages: [yaml]
weight: -1
updated: 2018-06-26
---

### 如何使用Docker加速器

打开 https://cr.console.aliyun.com/#/accelerator 找到 各自的 加速器 地址

我的是 https://ce0d6wdn2yph.mirror.aliyuncs.com


推荐安装1.10.0以上版本的Docker客户端。
您可以通过阿里云的镜像仓库下载：docker-engine、docker-ce
或执行以下命令：
    curl -sSL http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -

针对Docker客户端版本大于1.10的用户

```bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
    "registry-mirrors": ["https://ce0d6wdn2yph.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

参考：
- https://cr.console.aliyun.com/?spm=0.0.0.0.6qJBGw&accounttraceid=6af98742-1444-4d01-8c1c-007bde481948#/accelerator
- http://warjiang.github.io/devcat/2016/11/28/%E4%BD%BF%E7%94%A8%E9%98%BF%E9%87%8C%E4%BA%91Docker%E9%95%9C%E5%83%8F%E5%8A%A0%E9%80%9F/
- https://cr.console.aliyun.com/?spm=0.0.0.0.6qJBGw#/accelerator
- https://yq.aliyun.com/articles/29941
- https://cr.console.aliyun.com/?spm=5176.100239.blogcont29941.12.U7LEDI#/imageList

### 启动Docker守护进程 ###


- https://blog.csdn.net/hxpjava1/article/details/80505485
- https://blog.csdn.net/alinyua/article/details/81086124#_Docker_170
- https://yq.aliyun.com/articles/581105

#### 配置/etc/docker/daemon.json文件如下,注意,镜像地址与本文无关,可不配置 ####

因为，这里暂时不要去认证啥的，所以，只添加或修改 hosts 就行了。

```bash
{
  "hosts": ["tcp://0.0.0.0:2376","unix:///var/run/docker.sock"],
  "registry-mirrors": ["https://5ehijrnq.mirror.aliyuncs.com"]
}
```

#### systemctl restart docker 报错 ####

`sudo systemctl status docker` # 这里的输出，可以找到 docker.service 文件的位置，我们这里的是 /lib/systemd/system/docker.service

```bash
vagrant@ubuntu-xenial:~$ sudo vi /lib/systemd/system/docker.service
vagrant@ubuntu-xenial:~$ sudo systemctl daemon-reload
vagrant@ubuntu-xenial:~$ sudo systemctl stop docker
vagrant@ubuntu-xenial:~$ sudo systemctl start docker
vagrant@ubuntu-xenial:~$ sudo systemctl status docker
vagrant@ubuntu-xenial:~$ netstat -tnlp | grep 2376
tcp6       0      0 :::2376                 :::*                    LISTEN      -
vagrant@ubuntu-xenial:~$
```

#### 连接 Docker 守护进程 ####

```bash
DESKTOP-APB1HCJ% DOCKER_HOST=192.168.168.130:2376 docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                         PORTS               NAMES
24aa83bb32e3        hello-world         "/hello"            About an hour ago   Exited (0) About an hour ago                       flamboyant_gauss
DESKTOP-APB1HCJ%
```

可以在 `~/.zshrc` 中插入, 作为环境变量

```bash
DESKTOP-APB1HCJ% cat  ~/.zshrc | grep DOCKER
export DOCKER_HOST=tcp://127.0.0.1:2375
export DOCKER_HOST=tcp://192.168.168.130:2376
DESKTOP-APB1HCJ%
```


## ref
- https://blog.csdn.net/hxpjava1/article/details/80505485
- https://blog.csdn.net/alinyua/article/details/81086124#_Docker_170
