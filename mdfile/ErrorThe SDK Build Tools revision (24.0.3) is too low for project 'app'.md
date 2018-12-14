---
title: ErrorThe SDK Build Tools revision (24.0.3) is too low for project 'app'
tags: [android]
date: 2018-09-13
categories: android
---

ErrorThe SDK Build Tools revision (24.0.3) is too low for project 'app'
<!--more-->


## 问题原因

造成这个问题的原因可能是升级了Gradle插件的版本，也就是顶级build.gradle文件中声明的版本较高


## 解决办法



```
buildscript {
  ...
  dependencies {
    classpath 'com.android.tools.build:gradle:2.3.3'
  }
}

```
如上面的代码所示，在顶级build.gradle文件中声明gradle插件版本为2.3.3，那么就要求Gradle版本最低3.3，Build Tools版本最低25.0.0。 

至此结束啦~~
