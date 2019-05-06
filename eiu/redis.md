---
title: Redis
category: Redis
layout: 2017/sheet
---

### docker

```bash
docker pull redis:5.0.4
docker run --name some-redis -v /home/vagrant/redis-data:/data -p 6379:6379 -d redis:5.0.4 redis-server --appendonly yes
```

