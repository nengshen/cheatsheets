---
title: rvm
category: rvm
layout: 2017/sheet
---

## install rvm

```bash
which gpg2
sudo apt-get install gnupg2 -y
gpg2 --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
curl -sSL https://get.rvm.io | bash -s stable --rails
# 或者 curl -L https://get.rvm.io | bash -s stable
echo 'source ~/.rvm/scripts/rvm' >> ~/.bashrc
# 或者
echo 'source ~/.rvm/scripts/rvm' >> ~/.zshrc
```

https://github.com/rvm/rvm/issues/3830

## rvm install ruby

```bash
rvm requirements # 如果报错了，就认真看一下输入的提示，主要就是一个*.log文件
rvm install ruby
rvm install 2.6.0
```



## ref
- 
