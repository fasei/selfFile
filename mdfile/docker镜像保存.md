---
title: docker镜像保存
tags: [docker,基本操作]
date: 2018-11-29
categories: docker
---

docker镜像保存

<!--more-->

## docker镜像保存

-a :提交的镜像作者；
-c :使用Dockerfile指令来创建镜像；
-m :提交时的说明文字；
-p :在commit时，将容器暂停。
将容器a402222174a2 保存为新的镜像,并添加提交人信息和说明信息。

```
docker commit -a "runoob.com" -m "my apache" a404222274a2 my:v1
```

至此结束啦~~
