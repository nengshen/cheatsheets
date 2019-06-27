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

### Shell脚本逐行处理文本文件 

https://www.cnblogs.com/dwdxdy/archive/2012/07/25/2608816.html

不能使用 cat ,因为, 不是单行单行分隔, 而会是 空格 分隔.

```bash
while read line
do
    echo "File:${line}"
    dir="`echo "$line" | awk '{print $1}'`"
    weight="`echo "$line" | awk '{print $2}'`"
    echo "dir is : $dir, weight is : $weight"
    fileName="../content/$dir/_index.en.md"

    echo "---" > $fileName
    echo "date: 2019-06-27T15:15:15+08:00" >> $fileName
    echo "title: \"$dir\"" >> $fileName
    echo "weight: $weight" >> $fileName
    echo "keywords: " >> $fileName
    echo "description: \"$dir\"" >> $fileName
    echo "---" >> $fileName

done < kv.txt
```


## ref
- http://rickie622.blog.163.com/blog/static/212388112011213407503/
