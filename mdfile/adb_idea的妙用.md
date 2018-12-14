---
title: adb idea的妙用
tags: [android studio,工具,插件]
date: 2018-03-24
categories: android
---

# adb idea的妙用

> 在开发调试的时候，我们经常需要把当前项目app的数据清空，以测试用户第一次打开app时的情况。
通常我们需要在设置里面通过好几步繁琐的操作才能完成。特别是在测试机器里面，因为demo太多，要找到自己的app很难。
今天就来介绍一个能很快解决该问题的Android Studio插件：ADB IDEA。

<!--more-->

ADB IDEA是一个开源项目，地址：https://github.com/pbreault/adb-idea 。里面有项目介绍以及安装方法。

## 安装

依次打开references/Settings->Plugins->Browse Repositories，在输入框中输入adb，选择列表中的ADB Idea。点击安装。

## 使用

可以使用`Ctrl-Shift-A` (or Ctrl-Alt-Shift-A on Linux and Windows),在弹出的对话框中直接输入adb找到相关的操作。

so easy~