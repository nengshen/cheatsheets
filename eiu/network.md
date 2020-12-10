---
title: network-shadowsocks
category: Network
layout: 2017/sheet
---


## Docker安装Shadowsocks服务端

https://birdben.github.io/2017/01/19/Docker/Docker%E5%AE%9E%E6%88%98%EF%BC%88%E4%BA%8C%E5%8D%81%E4%B8%89%EF%BC%89Docker%E5%AE%89%E8%A3%85Shadowsocks/
https://github.com/birdben/birdDocker/tree/master/shadowsocks
https://my.oschina.net/u/1012033/blog/3001164
https://github.com/jinfeijie/canCross
## ubuntu 安装 Shadowsocks client

https://blog.huihut.com/2017/08/25/LinuxInstallConfigShadowsocksClient/

### Shadowsocks /etc/shadowsocks.json

```
{
  "server":"47.52.242.6",
  "local_address": "0.0.0.0",
  "local_port":1080,
  "server_port":1024,
  "password":"password",
  "timeout":300,
  "method":"aes-256-cfb"
}
```
local_address 的配置规则:

- 仅限本机使用, `local_address` 配置成 `127.0.0.0.1`
- 仅限通过本IP使用, `local_address` 配置成 `192.168.168.137`
- 所有IP可达本机使用, `local_address` 配置成 `192.168.168.137`

### 配置文件的路径改成自己的位置

```
ubuntu@ubuntu:~$ sudo cp /etc/shadowsocks.json /home/ubuntu/Software/Software/ShadowsocksConfig/
```

前端启动：`sslocal -c /home/ubuntu/Software/ShadowsocksConfig/shadowsocks.json`；
后端启动：`sslocal -c /home/ubuntu/Software/ShadowsocksConfig/shadowsocks.json -d start`；
后端停止：`sslocal -c /home/ubuntu/Software/ShadowsocksConfig/shadowsocks.json -d stop`；
重启(修改配置要重启才生效)：`sslocal -c /home/xx/Software/ShadowsocksConfig/shadowsocks.json -d restart`

### 开机自启

以下使用Systemd来实现shadowsocks开机自启。
```
sudo vim /etc/systemd/system/shadowsocks.service
```

### 启动报错 libcrypto.so.1.1: undefined symbol: EVP_CIPHER_CTX_cleanup

https://blog.csdn.net/blackfrog_unique/article/details/60320737

```
修改方法：

- 用vim打开文件：vim /usr/local/lib/python2.7/dist-packages/shadowsocks/crypto/openssl.py (该路径请根据自己的系统情况自行修改，如果不知道该文件在哪里的话，可以使用find命令查找文件位置)
- 跳转到52行（shadowsocks2.8.2版本，其他版本搜索一下cleanup）
- 进入编辑模式
- 将第52行libcrypto.EVP_CIPHER_CTX_cleanup.argtypes = (c_void_p,) 
改为libcrypto.EVP_CIPHER_CTX_reset.argtypes = (c_void_p,)
- 再次搜索cleanup（全文件共2处，此处位于111行），将libcrypto.EVP_CIPHER_CTX_cleanup(self._ctx) 
改为libcrypto.EVP_CIPHER_CTX_reset(self._ctx)
- 保存并退出
- 启动shadowsocks服务：service shadowsocks start 或 sslocal -c ss配置文件目录
问题解决
```

##
## (未成功) docker 安装 Shadowsocks client

https://github.com/sdcxyz/docker-shadowsocks


## privoxy

- http://einverne.github.io/post/2018/03/privoxy-forward-socks-to-http.html


## https ##

[使用 Certbot 为网站设置永久免费的 HTTPS 证书](https://jimmysong.io/posts/free-certificates-with-certbot/)
