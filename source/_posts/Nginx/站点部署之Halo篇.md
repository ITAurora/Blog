---
title: 站点部署之Halo篇
date: 2022-04-17 10:10:10
tags:
  - Halo
categories:
  - Halo
index_img: ../tnt/12.jpg
banner_img: ../tnt/12.jpg
excerpt: 摘要
---

## 前言
站点部署操作其实很简单，现在有很多镜像可以使用，像[wordpress](https://cn.wordpress.org/)，[Halo](https://halo.run/)，[Hexo](https://hexo.io/zh-cn/index.html)等等去官网都有部署教程，我这里只对Halo进行分析。
## 操作
Docker安装后
不行实在懒得说了，官网特详细
请移步官网：[Docker安装Halo](https://docs.halo.run/getting-started/install/docker)
算了 还是写详细一点吧
## 安装
写也是和官网差不多

**创建 工作目录**
```
mkdir ~/.halo && cd ~/.halo
```

**下载示例配置文件到 工作目录**
```
wget https://dl.halo.run/config/application-template.yaml -O ./application.yaml
```

**编辑配置文件，配置数据库或者端口等，如需配置请参考 配置参考**
```
vim application.yaml
```

**拉取最新的 Halo 镜像**
```
docker pull halohub/halo:1.6.0
```
查看最新版本镜像：https://hub.docker.com/r/halohub/halo ，官网推荐使用具体版本号的镜像，但也提供了 latest 标签的镜像，始终是最新的。

**创建容器**
```
docker run -it -d --name halo -p 8090:8090 -v ~/.halo:/root/.halo --restart=unless-stopped halohub/halo:1.6.0
```

此命令默认使用自带的 H2 Database 数据库。如需使用 MySQL，请参考：
[使用Docker部署Halo和MySql](https://docs.halo.run/getting-started/install/other/docker-mysql)

**注释：**
-it： 开启输入功能并连接伪终端
-d： 后台运行容器
--name： 为容器指定一个名称
-p： 端口映射，格式为 主机(宿主)端口:容器端口 ，可在 application.yaml 配置。**（这里后续在做域名反向代理的时候要用到，默认8090，可手动更改ip）**
-v： 工作目录映射。形式为：-v 宿主机路径:/root/.halo，后者不能修改。
--restart： 建议设置为 unless-stopped，在 Docker 启动的时候自动启动 Halo 容器。

打开 http://+ip:端口号 即可看到安装引导界面。
账号设置好之后  http://+ip:端口号 就是你的博客首页
http://+ip:端口号/admin 就是你的博客后台
没域名或者域名没备案的情况下只能通过ip访问
**提示**
站点信息填你的域名，域名可以后续备案以及再做反向代理，后续也可以在博客设置里面更改设置。
如果需要配置域名访问，建议先配置好反向代理以及域名解析再进行初始化。如果通过 http://ip:端口号 的形式无法访问，请到服务器厂商后台将运行的端口号添加到安全组，如果服务器使用了 Linux 面板，请检查此 Linux 面板是否有还有安全组配置，需要同样将端口号添加到安全组。

到此，Halo部署初步完成。
