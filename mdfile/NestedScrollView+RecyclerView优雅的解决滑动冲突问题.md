---
title: NestedScrollView+RecyclerView优雅的解决滑动冲突问题
tags: [android,recyclerView]
date: 2018-04-08
categories: android
---


在此之前，经历过ScrollView嵌套ScrollView滑动冲突，ScrollView与ListView嵌套滑动冲突等等，网上解决方法比较多暂不赘述了，RecyclerView出来已经差不多2年了，ListView可以说已经成为了过去式了，现在开发完全使用RecyclerView就行了。

<!--more-->

我亲自试验过，RecyclerView嵌套RecyclerView是不存在滑动冲突的，ScrollView嵌套RecyclerView也会存在显示不全的问题，滑动也有一点点粘连的感觉不是太流畅，NestedScrollView嵌套RecyclerView不会存在显示不全的问题，代码如下：

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.v4.widget.NestedScrollView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">
        
        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="@string/app_name"/>

        <android.support.v7.widget.RecyclerView
            android:id="@+id/recyclerView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>
        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="@string/app_name"/>
    </LinearLayout>

</android.support.v4.widget.NestedScrollView>

```


上面的代码只是简单的嵌套而已，但是还有一个小问题，触摸到RecyclerView的时候滑动还有些粘连的感觉，只需要在代码中设置

```
mRecyclerView.setHasFixedSize(true);
mRecyclerView.setNestedScrollingEnabled(false);
```

就可以完美的解决这个问题。

至此结束啦~~
