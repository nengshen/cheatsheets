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

### git diff old mode 100644 new mode 100755

执行git diff filename ,出现

```bash
old mode 100644 new mode 100755 的提示
```

```bash
git config --add core.filemode false
```

如果要全局设置, 则

```bash
git config --global core.filemode false
```
https://stackoverflow.com/questions/1257592/how-do-i-remove-files-saying-old-mode-100755-new-mode-100644-from-unstaged-cha
https://blog.csdn.net/ai2000ai/article/details/79628896

### git

## ref
- https://github.com/arslanbilal/git-cheat-sheet
- http://bilalarslan.me/git-cheat-sheet/
- https://blog.csdn.net/intergameover/article/details/50186239
