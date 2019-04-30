---
title: python-pyenv
category: Python
layout: 2017/sheet
---

## web

https://github.com/pyenv/pyenv

```bash
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
exec "$SHELL"
```



## pyenv-virtualenv

https://github.com/pyenv/pyenv-virtualenv

```bash
git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
exec "$SHELL"
```

## 常用命令

```bash
pyenv install --list # 列出可安装版本
pyenv install <version> # 安装对应版本
pyenv install -v <version> # 安装对应版本，若发生错误，可以显示详细的错误信息
pyenv versions # 显示当前使用的python版本
pyenv which python # 显示当前python安装路径
pyenv global <version> # 设置默认Python版本
pyenv local <version> # 当前路径创建一个.python-version, 以后进入这个目录自动切换为该版本
pyenv shell <version> # 当前shell的session中启用某版本，优先级高于global 及 local
```

## 使用virtualenv

```bash
pyenv virtualenv env # 从默认版本创建虚拟环境
pyenv virtualenv 3.6.4 env-3.6.4 # 创建3.6.4版本的虚拟环境
pyenv activate env-3.6.4 # 激活 env-3.6.4 这个虚拟环境
pyenv deactivate # 停用当前的虚拟环境
# 卸载
# pyenv uninstall py3-daily

# 自动激活
# 使用pyenv local 虚拟环境名
# 会把`虚拟环境名`写入当前目录的.python-version文件中
# 关闭自动激活 -> pyenv deactivate
# 启动自动激活 -> pyenv activate env-3.6.4
pyenv local env-3.6.4

pyenv uninstall env-3.6.4 # 删除 env-3.6.4 这个虚拟环境

pyenv virtualenv 3.7.0 py3-daily
pyenv activate py3-daily
# 关闭自动激活,停用虚拟环境
# pyenv deactivate
# 卸载
# pyenv uninstall py3-daily
```



## ref
- https://github.com/pyenv/pyenv
- https://eiu.app/post/python-pyenv-install-with-mac/
