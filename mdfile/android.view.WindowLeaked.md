---
title: android.view.WindowLeaked
tags: [android,view]
date: 2018-11-28
categories: android
---

android.view.WindowLeaked

<!--more-->
# android.view.WindowLeaked

leak 是泄露的意思，WindowLeaked 应该是窗体泄露， 碰到这种异常的原因我觉得是：在某个Dialog或者某个PopupWindow正在显示的时候我们去finish()了承载该Dialog(或PopupWindow)的Activity，所以抛出这种异常，因为这个Dialog(或PopupWindow)的WindowManager已经没有谁可以附属了，所以它的窗体管理器已经泄漏了。 

android.view.WindowLeaked一般会发生在Activity 与Dialog的显示。 

Activity 中create 一个Dialog，若你先关闭Dialog再关闭Activity就是正常的，若你先关闭Activity再关闭Dialog就会报错这个android.view.WindowLeaked错误了。 

分析这个原因是：Dialog是基于Activity而创建的：new ProgressDialog(this)；this 就是Activity。 Activtity先finish,那Dialog就没得依附了，所以就会报android.view.WindowLeaked。 

```
	android.view.WindowLeaked: Activity com.zonggou.recharge.OtpMainActivity has leaked window com.android.internal.policy.impl.PhoneWindow$DecorView{41713c40 V.E..... R.....ID 0,0-300,168} that was originally added here
```
解决：好多人都说这个是内存泄漏  我自己也弄了好久 终于找到了原因 哈哈 其实不是什么内存泄漏 
原因是 activity 和dialog同时显示 要先**dialog.dismiss() 后activity.finish()** 如果直接finish() 会出错 但不影响功能。