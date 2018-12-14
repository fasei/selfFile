---
title: TextView 默认字体大小
tags: [android,工具,TextView]
date: 2018-03-24
categories: android
---

# Android-TextView 默认字体大小


今天写代码的时候，突然来了兴致，TextView如果不指定textSize，那它的默认字体大小会是多少。

<!--more-->

查看TextView源码：
```
  	int textColorHighlight = 0;
    ColorStateList textColor = null;
    ColorStateList textColorHint = null;
    ColorStateList textColorLink = null;
        
	int textSize = 15;//默认字体
    String fontFamily = null;
    boolean fontFamilyExplicit = false;
    int typefaceIndex = -1;
    int styleIndex = -1;
    boolean allCaps = false;
    int shadowcolor = 0;
```

答案是15，我们可以清晰的看到源码中的textSize为15，单位是sp。