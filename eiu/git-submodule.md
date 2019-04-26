---
title: git-submodule
category: git
layout: 2017/sheet
---


### Changing remote repository for a git submodule – Stack Overflow ###

[reposted Changing remote repository for a git submodule – Stack Overflow](https://stackoverflow.com/questions/913701/changing-remote-repository-for-a-git-submodule)

These commands will do the work on command prompt without altering any files on local repository

```bash
git config --file=.gitmodules submodule.Submod.url https://github.com/username/ABC.git
git config --file=.gitmodules submodule.Submod.branch Development
git submodule sync
git submodule update --init --recursive --remote
```

Please look at the blog for screenshots: Changing GIT submodules URL/Branch to other URL/branch of same repository

### GIT Submodule HEAD detached from master

submodule 的 HEAD 是处于游离状态

#### 方法1 ####

默认下 submodule 的 HEAD 是处于游离状态的 (‘detached HEAD’ state)。所以在修改前，记得一定要用 git checkout master 将当前的 submodule 分支切换到 master，然后才能做修改和提交。

```bash
u@DESKTOP-APB1HCJ:~/.spacemacs.d/snippets$ git status
HEAD detached from 5962227
nothing to commit, working directory clean
u@DESKTOP-APB1HCJ:~/.spacemacs.d/snippets$ git branch -a
* (HEAD detached from 5962227)
  master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
u@DESKTOP-APB1HCJ:~/.spacemacs.d/snippets$
```

修改

```bash
git checkout master
git branch -a
git cherry-pick 5962227
git status
git aa
git ci -m "add markdown-mode"
git push origin master
git last
git log
git branch -a
```

https://blog.devtang.com/2013/05/08/git-submodule-issues/

#### 方法2 ####


https://stackoverflow.com/questions/18770545/why-is-my-git-submodule-head-detached-from-master

### 更新 submodule 的坑 ###

- https://blog.devtang.com/2013/05/08/git-submodule-issues/

### 修改 submodule 的坑 ###

- https://blog.devtang.com/2013/05/08/git-submodule-issues/

## ref
- https://stackoverflow.com/questions/913701/how-to-change-the-remote-repository-for-a-git-submodule
- https://dougbeal.com/2017/05/27/changing-remote-repository-for-a-git-submodule-stack-overflow/
- https://eiu.app/post/git-submodules-add-usage-delete/
- https://blog.devtang.com/2013/05/08/git-submodule-issues/
