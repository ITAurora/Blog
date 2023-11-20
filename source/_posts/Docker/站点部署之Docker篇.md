---
title: 站点部署之Docker篇
date: 2022-04-16 10:10:10
tags:
  - Docker
categories:
  - Docker
index_img: ../tnt/11.jpg
banner_img: ../tnt/11.jpg
excerpt: 摘要
---

## 前言
部署站点的插件有很多，之前我用过wordpress，使用宝塔面板一键部署。但是PHP语言维护过于艰辛（虽然我基本不动代码）我决定使用Docker来部署自己的站点，部署站点的意义不是为了部署站点而部署站点，要去学习其流程思想，要有宏观思想，要去学习一个项目从出生到上线再到展现到用户面前的整套流程，这样才有大局观，更能打开我们编程的思维。
## 导读
什么是Docker？
Docker 是一个开源的应用容器引擎，基于 Go 语言 并遵从 Apache2.0 协议开源。
我们编程硬件需要一台电脑，软件需要操作系统，跑程序需要代码的开发环境，而服务器上的程序也需要这些环境，不过不是现实中的环境，是一个虚拟的环境，而Docker就是一个虚拟环境容器。
标准答案：[Docker官网](https://www.docker.com/)
## Docker的三个概念
**镜像（Image）**：如果服务器比作一台电脑，而镜像就是此电脑的操纵系统。程序运行需要相应的环境，而镜像就是用来提供这种所需要的环境。
**容器（Container）**：一个轻量级的沙盒，像一个独立的电脑，里面包含着你的各种设置以及权限，类似于你对你电脑设置修改。容器是镜像创建的应用实例，一个程序对应一个容器，容器启动、停止、删除对应着程序的启动、停止、删除，各个容器之间相互隔离，互不影响。镜像本身是只读的，容器从镜像启动时，Docker在镜像的上层创建一个可写层，而镜像本身不变。
**仓库（Repository）**：镜像仓库，Docker用来集中存放镜像文件的地方。注意与注册服务器（Registry）的区别：注册服务器是存放仓库的地方，一般会有多个仓库；而仓库是存放镜像的地方，一般每个仓库存放一类镜像，每个镜像利用tag进行区分，比如Ubuntu仓库存放有多个版本（12.04、14.04等）的Ubuntu镜像。
## 进入正题
这里我服务器操作系统是centos，而且是精简版，其他版本参考：[Docker安装教程](https://www.runoob.com/docker/docker-tutorial.html)
## 安装Docker（centos版本）
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
此时Docker正式安装完成