---
title: linux
category: Linux
layout: 2017/sheet
---

### How to fix “Package is in a very bad inconsistent state” error?

https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error

### 免密码sudo

```bash
echo "{username} ALL = (root) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/{username}
echo "u ALL = (root) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/u
```

### 判断有没有wget

```bash
command -v wget >/dev/null 2>&1 || { echo >&2 "I require wget but it's not installed.  Aborting."; exit 1; }
```

### 把当前文件夹下的某文件路径加入到 其它路径下的某文件

如：把当前文件夹下的 zsh-syntax-highlighting/zsh-syntax-highlighting.sh 以字符串形式 echo 进 ~/.zshrc 文件

```bash
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

### 去除 w 属性

```bash
compaudit | xargs chmod g-w,o-w
```






## ref
- 