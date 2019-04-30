---
title: Linux-autojump
category: Linux
layout: 2017/sheet
---

## 安装 

```bash
git clone git://github.com/wting/autojump.git
cd autojump
./install.py or ./uninstall.py
# 根据提示
[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh
autoload -U compinit && compinit -u
```

## autojump_chpwd:4: nice(5) failed: operation not permitted

https://github.com/wting/autojump/issues/474

add this to your `~/.zshrc`:

```
unsetopt BG_NICE
```

## ref
- https://github.com/wting/autojump
- [Linux 懒人工具 - autojump](https://www.jianshu.com/p/15f0ffaa88d7)
