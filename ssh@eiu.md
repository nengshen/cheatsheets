---
title: ssh@tom
category: CLI
layout: 2017/sheet
---

### ssh -i 连接

首先确保文件权限400(否则连接不了) 

```bash
chmod 400 valueaddedinsingpo.pem
ssh -i "vachain_competition.pem" ubuntu@ec2-13-125-197-97.ap-northeast-2.compute.amazonaws.com
ssh -i vachain_competition.pem -o IdentitiesOnly=yes ubuntu@ec2-13-125-197-97.ap-northeast-2.compute.amazonaws.com
ssh -i vachain_competition.pem -o 'IdentitiesOnly yes' ubuntu@ec2-13-125-197-97.ap-northeast-2.compute.amazonaws.com
```