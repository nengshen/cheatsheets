---
title: powershell
category: windows
layout: 2017/sheet
---

### Windows中查找命令的路径 (类似Linux中的which命令)

#### Get-Command

In PowerShell you have Get-Command and its alias gcm which does the same if you pass an argument (but also works for aliases, cmdlets and functions in PowerShell):

```bash
PS C:\Users\Joey> Get-Command where
 
CommandType     Name          Definition
-----------     ----          ----------
Alias           where         Where-Object
Application     where.exe     C:\Windows\system32\where.exe
```

The first returned command is the one that would be executed.


## ref
- https://blog.csdn.net/sforiz/article/details/80540625
