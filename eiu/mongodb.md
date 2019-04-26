---
title: mongodb
category: mongodb
layout: 2017/sheet
---


### MongoDB 用户名密码登录

https://www.jianshu.com/p/79caa1cc49a5

### 查看当前库下的账户 :

```
> use admin
switched to db admin
> show users
```
### 查看全局所有账户 :

```
>  use admin
switched to db admin
> db.auth('admin','123456')
1
> db.system.users.find().pretty()
```

## ref
- https://www.jianshu.com/p/79caa1cc49a5
- https://blog.csdn.net/u010649766/article/details/78498130
