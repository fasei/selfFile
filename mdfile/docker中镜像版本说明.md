---
title: docker中wanc镜像版本说明
tags: [docker,wanc镜像版本]
date: 2018-12-07
categories: docker
---

docker中wanc镜像版本说明

<!--more-->

# wanc hexo镜像
## wanc:1.1 

1. 安装了openssh 
2. 安装了hexo
3. 启动需要端口映射
4. 映射端口4000到400，便于外面访问hexo
```
docker run -ti -p 4000:400 -p 222:222 wanc:1.0 /bin/bash
```
5. hexo 和openssh 端口映射
```
docker run -ti -p 4000:4000 -p 222:222 -p 21:21 wanc:1.0 /bin/bash
```
6. 启动openssh远程服务
```
service ssh start
```
7. 远程密码  xiaoyuaynuan1314
## wanc:1.1
1. ubuntu系统
2. 可以远程：xiaoyuanyuan1314
至此结束啦~~

# base 基础镜像
## base：1.0
1. wanc：1.1


# cms lamp镜像
## cms:1.0
1. 增加了php的安装，完成了lamp
2. 手动启动apache2服务： service apache2 start
## cms:1.0 
1. 安装了apache2
2. 安装了mysql可以远程密码：xiaoyuaynuan1314
3. base：1.0
