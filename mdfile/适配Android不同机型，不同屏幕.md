---
title: 适配Android不同机型，不同屏幕
tags: [android,适配]
date: 2018-03-24
categories: android
---

# 适配Android不同机型，不同屏幕

借鉴drawable文件夹，values使用dimens控制字体大小、边距大小，达到适配的效果。

<!--more-->

## 分辨率说明
首先查看密度 与分辨率的关系图

|    密度    |       ldpi|mdpi |     hdpi|xhdpi |xxhdpi|
|:-------:|:-------------:|:----------|:----------:|:----------:|
|密度值|    120	    |   160  |240|320|480|
|代表分辨率|	240*320|	320*480|480*800|	720*1280|	1080*1920|

## 创建不同的位图（Android官方介绍）

- xxxhdpi: 5.0  500*500 
- xxhdpi: 3.0    300*300
- xhdpi：2.0    200*200
- hdpi：1.5     150*150
- mdpi：1.0（baseline）   100*100
- ldpi：0.75    75*75 

查看不同分辨率下图片的数值

|    文件夹名称    |       比例|图片大小 |     屏幕宽度|DPI值 |分辨率举例|
|:-------:|:-------------:|:----------|:----------:|:----------:|
|drawable-xxxhdpi|     5.0	    |   500*500   |1440左右|640dpi|2560*1440（Nexus6）|
|drawable-xxxhdpi|	5.0|	500*500|1440左右|	640dpi|	2560*1440（Nexus6）|
|drawable-xxhdpi|3.0|	300*300|1080左右	|480dpi	|1080*1920|
|drawable-xhdpi|2.0|	200*200	|720左右|	320dpi	|720*1280|
|drawable-hdpi|1.5	|150*150|	480左右|	240dpi	|480*800,480*854,540*960|
|drawable-mdpi|1.0（BaseLine）|	100*100|	360左右	|160dpi	|320*480|
|drawable-ldpi|0.75	|75*75|	240左右	 	 |-|-|

## values适配
借鉴drawable文件夹，依次创建values，values-mdpi, values-hdpi，values-xhdpi, values-xxhdpi, values-xxxhdpi。 (鉴于现在ldpi的机型很少，就直接使用默认的values来做适配)。

|文件夹名称	|字体大小sp|	距离大小dp|	手机输出值（字体大小）	|手机显示值（距离大小）|
|:-------:|:-------------:|:----------|:----------:|:----------:|
|values-xxxhdpi|	50	|50	|175.0	|175.0|
|values-xxhdpi	|30|	30	|90.0|	90.0|
|values-xhdpi	|20|	20|	40.0|	40.0|
|values-hdpi	|15|	15|	22.5	|22.5|
|values-hdpi(854*480)	|-|-|25.87	|22.5|
|values-mdpi	|10|	10|	10.0|	10.0|
|values-ldpi	|7.5|	7.5|	5.625|	5.625|

至此结束啦~~
