---
title: Git
category: Git
layout: 2017/sheet
---

### Check your information 

```bash
git config --global --list
```

### Delete all changes in the Git repository, but leave unstaged things 

```bash
git checkout .
```

### Delete all changes in the Git repository, including untracked files 

```bash
git clean -f
```

### git客户端连接ssh端口不是22的git仓库 ###

```bash
git clone http://192.168.168.164:5080/FED/lvchuang-web.git
git clone ssh://git@192.168.168.164:5022/FED/lvchuang-web.git
```

- https://blog.csdn.net/intergameover/article/details/50186239

## ref
- https://github.com/arslanbilal/git-cheat-sheet
- http://bilalarslan.me/git-cheat-sheet/
- https://blog.csdn.net/intergameover/article/details/50186239
