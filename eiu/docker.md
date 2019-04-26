---
title: docker-compose
category: Devops
layout: 2017/sheet
prism_languages: [yaml]
weight: -1
updated: 2018-06-26
---

### 如何使用Docker加速器

打开 https://cr.console.aliyun.com/#/accelerator 找到 各自的 加速器 地址

我的是 https://ce0d6wdn2yph.mirror.aliyuncs.com


推荐安装1.10.0以上版本的Docker客户端。
您可以通过阿里云的镜像仓库下载：docker-engine、docker-ce
或执行以下命令：
    curl -sSL http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -

针对Docker客户端版本大于1.10的用户

```bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
    "registry-mirrors": ["https://ce0d6wdn2yph.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

参考：
- https://cr.console.aliyun.com/?spm=0.0.0.0.6qJBGw&accounttraceid=6af98742-1444-4d01-8c1c-007bde481948#/accelerator
- http://warjiang.github.io/devcat/2016/11/28/%E4%BD%BF%E7%94%A8%E9%98%BF%E9%87%8C%E4%BA%91Docker%E9%95%9C%E5%83%8F%E5%8A%A0%E9%80%9F/
- https://cr.console.aliyun.com/?spm=0.0.0.0.6qJBGw#/accelerator
- https://yq.aliyun.com/articles/29941
- https://cr.console.aliyun.com/?spm=5176.100239.blogcont29941.12.U7LEDI#/imageList

## ref
- 
