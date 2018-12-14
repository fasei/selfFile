---
title: docker删除镜像
tags: [docker,基本操作]
date: 2018-11-28
categories: docker
---

docker删除镜像的基本操作

<!--more-->

## 查看镜像 docker images

```
rt@123:~# docker images
REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
192.168.0.1/jii/jenkins                    1.0.1              3391ef1391f6        18 hours ago        206 MB
192.168.0.1/you/tom                        1.0.8              f8ab12e03d53        22 hours ago        276 MB
192.168.0.1/you/tom                        1.0.9              f8ab12e03d53        22 hours ago        276 MB
```

## 删除镜像，会报错
```
rt@123:~# docker rmi f8ab12e03d53
Error response from daemon: conflict: unable to delete f8ab12e03d53 (must be forced) - image is referenced in multiple repositories
```

仔细观察，发现f8ab12e03d53这个镜像id指向了两个repository，因此无法删除


## 删除时可以用repository和tag的方式来删除

```
rt@123:~# docker rmi 192.168.0.1/you/tom:1.0.8
Untagged:192.168.0.1/you/tom:1.0.8

```

## 再次查看镜像，1.0.8的就被删除了。

```
rt@123:~# docker images
REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
192.168.0.1/jii/jenkins                    1.0.1              3391ef1391f6        18 hours ago        206 MB
192.168.0.1/you/tom                        1.0.9              f8ab12e03d53        22 hours ago        276 MB

```

至此结束啦~~
