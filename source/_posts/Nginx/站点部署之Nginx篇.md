---
title: 站点部署之Nginx篇
date: 2022-04-17 10:10:10
tags:
  - Nginx
categories:
  - Nginx
index_img: ../tnt/12.jpg
banner_img: ../tnt/12.jpg
excerpt: 摘要
---



## 导读
Nginx是什么？
菜鸟教程有很详细的图解：[Nginx图解](https://www.runoob.com/w3cnote/nginx-setup-intro.html)
英语能力好的可以去官网阅读：[Nginx官网](https://nginx.org/en/)
翻译过来就是说：
Nginx是一款轻量级的Web 服务器/反向代理服务器及电子邮件（IMAP/POP3）代理服务器，并且在BSD-like 协议下发行。
## 安装Nginx
先下载Nginx包：[下载](http://ultracode.cn:1111/#s/8umAf2qQ)
放到你服务器的root目录下
**在 /usr/local/ 下创建 nginx 文件夹并进入**
```
cd /usr/local/
mkdir nginx
cd nginx
```
**将 Nginx 安装包解压到 /usr/local/nginx 中即可**
```
 tar zxvf /root/nginx-1.17.10.tar.gz -C ./
```
**解压完之后，你的 /usr/local/nginx 目录中会出现一个 nginx-1.17.10 的目录**
**安装需要的依赖**
```
 yum -y install pcre-devel
 yum -y install openssl openssl-devel
```

**安装nginx**
```
cd nginx-1.17.10 
./configure
make 
make install
```
**安装完成后，Nginx的可执行文件位置位于**
/usr/local/nginx/sbin/nginx

**启动nginx**

直接执行

```
 /usr/local/nginx/sbin/nginx
```
停止nginx服务

```
/usr/local/nginx/sbin/nginx -s stop
```

如果修改了配置文件后想重新加载Nginx，可执行:

```
/usr/local/nginx/sbin/nginx -s reload
```

配置文件路径
/usr/local/nginx/conf/nginx.conf
此时你要是访问你的域名或者ip会出现welcome to nginx界面 说明你的nginx已经安装好了
后面配置在/usr/local/nginx/conf/nginx.conf文件里进行配置
把原有数据删掉，修改为
```
upstream halo {
  server 127.0.0.1:8090;
}
server {
  listen 80;
  listen [::]:80;
  server_name www.yourdomain.com;
  client_max_body_size 1024m;
  location / {
    proxy_pass http://halo;
    proxy_set_header HOST $host;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }
}
```
127.0.0.1:8090替换为  你的服务器公网ip:你设置的Halo端口
www.yourdomain.com  替换为你的域名
：wq保存退出

访问你的域名 会出现你的博客首页
如果出现403，修改权限，在/usr/local/nginx/conf/nginx.conf文件最上端添加一行代码
```
user root；
```
从新加载nginx即可
```
/usr/local/nginx/sbin/nginx -s reload
```
至此，网站的反向代理配置结束。