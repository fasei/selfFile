---
title: HorizontalScrollView嵌套RecyclerView展示不完全问题
tags: [android,horizontalScrollView,recyclerView]
date: 2018-04-23
categories: android
---

项目中有个HorizontalScrollView嵌套RecycleView的列表在华为荣耀8（android7.0系统）上展示不完全（横向滑动展示不完全） 

<!--more-->

## 解决方法

在RecycleView外层嵌套一个**RelativeLayout**里面添加:

```
android:descendantFocusability=”blocksDescendants”
```

这个属性即可

这个属性含有三个值如下 
**beforeDescendants：viewgroup**会优先其子类控件而获取到焦点 
**afterDescendants：viewgroup**只有当其子类控件不需要获取焦点时才获取焦点 
**blocksDescendants：viewgroup**会覆盖子类控件而直接获得焦点

至此结束啦~~
