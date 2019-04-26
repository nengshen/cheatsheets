---
title: mysql
category: mysql
layout: 2017/sheet
---

### 时间

#### 建表sql 使用 current_timestamp 代替 NULL

```
  `create_date` timestamp NULL DEFAULT NULL COMMENT '创建时间',
  `update_date` timestamp NULL DEFAULT NULL COMMENT '更新时间',
```

修改成
  
```
  `create_date` timestamp NULL DEFAULT current_timestamp() COMMENT '创建时间',
  `update_date` timestamp NULL DEFAULT NULL ON UPDATE current_timestamp() COMMENT '更新时间',
```

## ref
- 
