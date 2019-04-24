---
title: cmd
category: windows
layout: 2017/sheet
---

### Windows中查找命令的路径 (类似Linux中的which命令)

#### where

where is a direct equivalent:

```bash
C:\Users\Joey>where cmd
C:\Windows\System32\cmd.exe
```

Note that in PowerShell where itself is an alias for Where-Object, thus you need to usewhere.exe in PowerShell.

#### for

In cmd you can also use for:

```bash
C:\Users\Joey>for %x in (powershell.exe) do @echo %~$PATH:x
C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
```


## ref
- https://blog.csdn.net/sforiz/article/details/80540625
