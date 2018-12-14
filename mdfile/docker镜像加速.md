---
title: docker镜像加速
tags: [docker,基本操作]
date: 2018-11-28
categories: docker
---

docker镜像加速

<!--more-->

## docker镜像加速

1. 我这里用的是阿里云的->容器镜像服务->镜像加速器 
2. 首先登陆阿里云获取加速地址：我的加速地址:https://wyv0qi1c.mirror.aliyuncs.com
3. 然后在powershell 输入如下命令

```
docker-machine ssh default 
sudo sed -i "s|EXTRA_ARGS='|EXTRA_ARGS='--registry-mirror=https://wyv0qi1c.mirror.aliyuncs.com |g" /var/lib/boot2docker/profile 
exit 
docker-machine restart default
```


至此结束啦~~
