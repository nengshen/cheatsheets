---
title: Gitlab@tom
category: CLI
layout: 2017/sheet
---


### Push to create a new project 

If you have access to that namespace, we will automatically create a new project under that GitLab namespace with its visibility set to Private by default 

```bash
## Git push using SSH
git push --set-upstream git@gitlab.example.com:namespace/nonexistent-project.git master

## Git push using HTTP
git push --set-upstream https://gitlab.example.com/namespace/nonexistent-project.git master
```