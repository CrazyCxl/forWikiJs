---
title: adb
description: adb doc
published: true
date: 2020-07-27T08:29:08.397Z
tags: adb android
---

# 常用命令
## 列出设备
```
adb devices
```
## 导入导出文件
```
adb pull  /sdcard/xxx  /Users/xxxx/xxx.tx
adb push  /Users/xxxx/xxx.txt   /sdcard/xxx
```
## 导出UI信息
```
adb shell uiautomator dump /sdcard/ui.xml
```

# 通过Tcp连接
```
adb tcpip 10555
adb connect 10.6.16.126:10555
```