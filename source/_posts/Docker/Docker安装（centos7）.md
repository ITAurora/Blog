---
title: Docker安装（centos7）
date: 2022-02-18 10:10:10
tags:
  - Docker
categories:
  - Docker
index_img: ../tnt/9.jpg
banner_img: ../tnt/9.jpg
excerpt: 摘要
---
<meta name="referrer" content="no-referrer"/>

# Docker安装（centos7）

安装命令:
```
yum install docker
```

设置开机自动启动:
```
service docker start
```

查看版本:
```
docker version
```

修改docker仓库地址:
```
vi /etc/docker/daemon.json
```

修改配置文件为：
```
{ “registry-mirrors”: [“https://registry.docker-cn.com”], “live-restore”: true }
```
