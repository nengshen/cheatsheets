---
title: Cron
category: CLI
layout: 2017/sheet
updated: 2017-08-26
weight: -3
---

### Example2

```bash
$ crontab -l
#SHELL=/usr/bin/bash
#PATH=/usr/local/bin:/usr/bin

#m      h       dom     mon     dow     user command
0	2	*	*	*	sudo yum update -y >>/home/tom/log/crontab/update.log
30	22	*	*	1-5	cd /home/jlch/registry/tramitter_client && node ./index.js >> index.js.log 2>&1
```
