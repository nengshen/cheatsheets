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

