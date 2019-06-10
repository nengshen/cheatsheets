---
title: nodejs-pm2
category: Node.js
layout: 2017/sheet
---


## pm2

https://github.com/Unitech/PM2/

https://pm2.io/

https://app.pm2.io

http://pm2.keymetrics.io

## pm2 与 环境变量的设置

https://github.com/eiuapp/tl-lvchuang-src-server/commit/d7ff45fcd001f58099b2380518af17e209784faf

index.yml 

```yaml
apps:
  - script   : ./dummyServer.js
    name     : 'dummy-server'
    watch  : true
    env    :
      NODE_ENV: development
      port: 3022
    env_production:
      NODE_ENV: production
      port: 3012
    instances: 1
  - script : ./index.js
```

这里的 index.yml 设置的 env.port , 可以在程序文件中 通过  process.env.port 获取. 从而实现,不需要修改代码,只需要修改 `index.yml` 文件,就达到改变端口的目的.

如果 `index.yml` 中设置的是 `PORT: 3022`, 那程序中 就是 `process.env.PORT` .


## pm2 reload 重启 应用

```bash
pm2 reload index.yml --only dummy-server
```

## PM2+ Monitoring

https://app.pm2.io


## pm2 start

```bash
pm2 start ecosystem.config.js --only development && pm2 logs development
pm2 start ecosystem.config.js --only index --env production && pm2 logs index
```

## pm2 stop

```bash
pm2 stop index
pm2 stop index # && pm2 start ecosystem.config.js --only index && pm2 logs index
```

## ecosystem.config.js

如果希望在 index.js 上启动2种形式, 且还要方便调试, 那么可以这样做

在 app [] 中设置2个 script: "./index.js" 的文件, 但是其它选项不同.

```bash
 {
      name: 'index',
      script: './index.js',
      // args: 'one two',
      instances: 1,
      autorestart: true,
      watch: false,
      max_memory_restart: '300M',
      restart_delay: 3000,
      env: {
        NODE_ENV: 'development',
        PORT: 3011
      },
      env_test: {
        NODE_ENV: 'test',
        PORT: 3012
      },
      env_production: {
        NODE_ENV: 'production',
        PORT: 3011
      }
    },
    {
      name: 'development',
      script: './index.js',
      // args: 'one two',
      instances: 1,
      autorestart: true,
      watch: true,
      max_memory_restart: '300M',
      restart_delay: 3000,
      env: {
        NODE_ENV: 'development',
        PORT: 3013
      },
      env_test: {
        NODE_ENV: 'test',
        PORT: 3012
      },
      env_production: {
        NODE_ENV: 'production',
        PORT: 3011
      }
    }
```

这样呢, 
- pm2 start ecosystem.config.js --only index 就可以不 watch  
- pm2 start ecosystem.config.js --only development 就可以watch, 
- 且各自的port不同

如果这时,想用 vscode 来 debug, 则只需要 pm2 stop development, 然后 F5 就可以了, 很方便




## pm2设置开机自启动命令

- pm2 startup，这个命令会在系统 `/etc/systemd/system/` 路径下生成一个 `pm2-root.service` 文件用来开机启动 pm2 服务。
- pm2 save, 保存当前 pm2 运行的各个应用保存到 `/root/.pm2/dump.pm2` 下，开机重启时读取该文件中的内容启动相关应用。

