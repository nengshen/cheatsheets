---
title: spacemacs-docker
category: spacemacs
layout: 2017/sheet
---

spacemacs + docker 安装使用

## docker中安装使用spacemacs 


想玩emacs27很简单，上Docker啊

xhost +local:root # WARN: this comes with security issues 

docker run -it --rm -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix silex/emacs

https://github.com/Silex/docker-emacs

