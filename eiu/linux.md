---
title: linux
category: Linux
layout: 2017/sheet
---

### How to fix “Package is in a very bad inconsistent state” error? ###

https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error

### 免密码sudo ###

```bash
echo "{username} ALL = (root) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/{username}
echo "u ALL = (root) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/u
```

### 判断有没有wget ###

```bash
command -v wget >/dev/null 2>&1 || { echo >&2 "I require wget but it's not installed.  Aborting."; exit 1; }
```

### 把当前文件夹下的某文件路径加入到 其它路径下的某文件 ###

如：把当前文件夹下的 zsh-syntax-highlighting/zsh-syntax-highlighting.sh 以字符串形式 echo 进 ~/.zshrc 文件

```bash
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

### 去除 w 属性 ###

```bash
compaudit | xargs chmod g-w,o-w
```

### dos2unix ###

#### install ####

https://www.jianshu.com/p/d5eb279de997

```bash
sudo apt-get install tofrodos
sudo ln -s /usr/bin/todos /usr/bin/unix2dos 
sudo ln -s /usr/bin/fromdos /usr/bin/dos2unix 
```

#### dos2unix ####

把文档全转成 unix end-of-line

```bash
dos2unix ./*/*.md
```







### linux tar压缩排除某个文件夹 ###

如我们输入 tomcat/lo 的时候按tab键，命令行会自动生成 tomcat/logs/ ，对于目录，最后会多一个 “/”

这里大家要注意的时候，在我们使用tar 的--exclude 命令排除打包的时候，不能加“/”，否则还是会把logs目录以及其下的文件打包进去。

错误写法：

```bash
tar -zcvf tomcat.tar.gz --exclude=tomcat/logs/ --exclude=tomcat/libs/ tomcat
```bash

正确写法：

```bash
tar -zcvf tomcat.tar.gz --exclude=tomcat/logs --exclude=tomcat/libs tomcat
```

## ref
- 
