---
title: spacemacs-emacs
category: spacemacs
layout: 2017/sheet
---

spacemacs-emacs

## How to Install Emacs 26.2 in Ubuntu: ##

https://www.jianshu.com/p/612cbc1b0d63


### install emacs (no configure) ###

1. Open terminal either via Ctrl+Alt+T keyboard shortcut or by searching for “Terminal” from start menu. When it opens, run command to add the PPA repository:
```bash
sudo add-apt-repository ppa:kelleyk/emacs
```
Type user password (no asterisk feedback due to security reason) when prompts and hit Enter.

2. Then install Emacs26 either via Synaptic package manager, or by running following commands one by one in terminal:

```bash
sudo apt update
sudo apt install emacs26
```

How to Remove:

To remove Emacs26, open terminal and run commands:

```bash
sudo apt remove --autoremove emacs26 emacs26-nox
```

- http://ubuntuhandbook.org/index.php/2019/04/gnu-emacs-26-2-released-install-in-ubuntu-18-04/
- https://www.tecrobust.com/install-emacs-linux-editor-ubuntu/



### install emacs (configure) ###

https://www.admintome.com/blog/install-emacs-26-1-on-ubuntu/

### 安装，没有问题。但是，使用的时候有问题。

https://eiuapp.github.io/post/ubuntu-spacemacs/

## setup


https://acemerlin.github.io/posts/%E6%9D%82%E8%B0%88/2018-04-09-windows-10-bash-wsl-spacemacs-setup/
上面的文章，应该是比较接近的。windows-10-bash-wsl中安装spacemacs的配置







## disable spacemacs buffer on startup

https://github.com/syl20bnr/spacemacs/issues/6899#issuecomment-364684148

```
(defun dotspacemacs/user-config ()
  (kill-buffer "*spacemacs*"))
```
