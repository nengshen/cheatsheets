---
title: Bash scripting
category: CLI
layout: 2017/sheet
tags: [Featured]
updated: 2019-03-23
keywords:
  - Variables
  - Functions
  - Interpolation
  - Brace expansions
  - Loops
  - Conditional execution
  - Command substitution
---


History
-------

Miscellaneous
-------------

### basename

basename取本shell的文件名

```bash
/home/ope3/.anacon2/bin/python run_today.py  >> ~/log/`basename $0`.log  2>&1
```

### 当前使用的SHELL

查看当前使用的shell
```bash
ps $$
ps |  grep $$  |  awk '{print $4}'
```

## ref
- http://rickie622.blog.163.com/blog/static/212388112011213407503/
