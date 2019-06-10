---
title: python-file
category: Python
layout: 2017/sheet
---

python file

## python 读取TXT内内容，按行存入list

```python
def ReadTxtName(rootdir):
    lines = []
    with open(rootdir, 'r') as file_to_read:
        while True:
            line = file_to_read.readline()
            if not line:
                break
            line = line.strip('\n')
            lines.append(line)
    return lines

resultpath='E:\\zhanglong\\20181115_1\\little\\facecalib.txt'
lineslist=ReadTxtName(resultpath)
```

https://blog.csdn.net/xiaohuaibao/article/details/84345038

