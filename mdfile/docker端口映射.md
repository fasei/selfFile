---
title: docker端口映射
tags: [docker,基本操作]
date: 2018-12-03
categories: docker
---

docker端口映射

<!--more-->

## docker端口映射

1. 我在容器中运行hexo，需要访问4000端口，可以将4000端口映射出来

```
docker run -ti -p 4000:400 wanc:1.0 /bin/bash
```

将4000端口映射到400 端口，然后在宿主电脑访问400端口即可


至此结束啦~~
