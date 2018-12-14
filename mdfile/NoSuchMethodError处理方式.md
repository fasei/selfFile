---
title: NoSuchMethodError处理方式
tags: [android,NoSuchMethodError,冲突]
date: 2018-04-27
categories: android
---

## Bug:

java.lang.NoSuchMethodError: No static method setLayoutDirection(Landroid/graphics/drawable/Drawable;I)V in class Landroid/support/v4/graphics/drawable/DrawableCompat; 
然后出现了这个：java.lang.NoClassDefFoundError: android.support.v7.widget.RecyclerView$SavedState

<!--more-->

## 解决方法

修改gradle中内容：

```
compile ('com.android.support:support-v4:23.4.0'){
  force = true;
}
compile('com.android.support:recyclerview-v7:23.4.0') {
  exclude module: 'support-v4'
}```

至此结束啦~~
