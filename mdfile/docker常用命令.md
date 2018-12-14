---
title: docker常用命令
tags: [docker,基本操作]
date: 2018-11-29
categories: docker
---

docker常用命令

<!--more-->
## 端口说明
hexo 使用的4000 映射为4000
openssh使用的端口为222 映射为222
可以使用IP:HostPort:ContainerPort格式指定映射使用一个特定地址：




## 常用命令

1. 映射端口4000到400，便于外面访问hexo
```
docker run -ti -p 4000:4000 -p 21:21 wanc:1.0 /bin/bash
```
2. hexo 和openssh 端口映射
```
docker run -ti -p 4000:4000 -p 222:222 -p 21:21 wanc:1.0 /bin/bash

 docker run -ti -p 4000:4000 -p 222:222 -p 21:21 -p 3306:3306 -p 80:80 base:1.0 /bin/bash
```
3. 启动openssh远程服务
```
service ssh start
```
至此结束啦~~

docker images说明：
1、base 基础库，包含远程的软件和hexo
2、wanc 同base未做修改