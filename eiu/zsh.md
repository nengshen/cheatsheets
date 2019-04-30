---
title: zsh
category: CLI
layout: 2017/sheet
---

### plugins

https://segmentfault.com/a/1190000018093021
https://www.jianshu.com/p/9189eac3e52d

下列必须安装

强烈建议把这些插件的用法，看一遍

```
git 
extract 
z 
autojump 
[zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
zsh-autosuggestions
web-search
```

视个人情况安装

```bash
kubectl
sublime
common-aliases
```





### Insecure completion-dependent directories detected

```bash
DESKTOP-APB1HCJ% zsh
[oh-my-zsh] Insecure completion-dependent directories detected:
drwxrwxrwx 1 u u 4096 Apr 27 12:29 /mnt/c/Users/a/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting

[oh-my-zsh] For safety, we will not load completions from these directories until
[oh-my-zsh] you fix their permissions and ownership and restart zsh.
[oh-my-zsh] See the above list for directories with group or other writability.

[oh-my-zsh] To fix your permissions you can do so by disabling
[oh-my-zsh] the write permission of "group" and "others" and making sure that the
[oh-my-zsh] owner of these directories is either root or your current user.
[oh-my-zsh] The following command may help:
[oh-my-zsh]     compaudit | xargs chmod g-w,o-w

[oh-my-zsh] If the above didn't help or you want to skip the verification of
[oh-my-zsh] insecure directories you can set the variable ZSH_DISABLE_COMPFIX to
[oh-my-zsh] "true" before oh-my-zsh is sourced in your zshrc file.

~/.zshrc.local
N/A: version "v11.14.0 -> " is not yet installed.

You need to run "nvm install v11.14.0" to install it before using it.
zsh compinit: insecure directories, run compaudit for list.
Ignore insecure directories and continue [y] or abort compinit [n]? ^C%
```

根据提示 去除 w 权限

```bash
DESKTOP-APB1HCJ% cd .oh-my-zsh/custom/plugins
DESKTOP-APB1HCJ%  compaudit | xargs chmod g-w,o-w
There are insecure directories:
DESKTOP-APB1HCJ% ls
example  zsh-syntax-highlighting
DESKTOP-APB1HCJ% ll
total 0
drwxr-xr-x 1 u u 4096 Apr 27 12:36 .
drwxr-xr-x 1 u u 4096 Apr 19 10:53 ..
drwxr-xr-x 1 u u 4096 Apr 19 10:53 example
drwxr-xr-x 1 u u 4096 Apr 27 12:29 zsh-syntax-highlighting
DESKTOP-APB1HCJ% zsh
~/.zshrc.local
N/A: version "v11.14.0 -> " is not yet installed.

You need to run "nvm install v11.14.0" to install it before using it.
0.34.0
N/A: version "v11.14.0 -> N/A" is not yet installed.

You need to run "nvm install v11.14.0" to install it before using it.
DESKTOP-APB1HCJ%
```


### Also see

- [Bash cheatsheet](./bash)

Zsh is mostly compatible with Bash, so most everything in Bash's cheatsheet also applies.
