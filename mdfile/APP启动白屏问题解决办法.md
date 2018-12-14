---
title: APP启动白屏问题解决办法
tags: [android,白屏]
date: 2018-05-02
categories: android
---

android app在启动的时候会有一个白屏或者黑屏的效果，非常恶心，现就此问题分析解决。
<!--more-->


## 问题原因

**Activity只能到onResume时，才能展示到前台**。onCreate中的setContentView();方法有耗时操作，所以，如果为MainActivity设置背景的话，无论onCreate-onResume速度多快，都会出现短暂的白屏或者黑屏（视application的background属性而定）。


## 解决办法

找到清单文件中设置主题这句话，新增主题或者修改默认主题即可，修改时一般有以下几种方式。

1、背景修改为透明(推荐)

```
<item name="android:windowIsTranslucent">true</item>

```

2、设置一张背景图(一闪而过，一般选择和启动页颜色相近的图片)

```
<item name="android:windowBackground">@drawable/bg</item>

```

3、设置与启动页相近的背景颜色

```
<item name="android:windowBackground">@android:color/black</item>

```

至此结束啦~~
