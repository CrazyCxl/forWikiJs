---
title: adb
description: adb doc
published: true
date: 2024-01-01T03:13:07.968Z
tags: adb android
editor: markdown
dateCreated: 2020-07-27T08:29:08.397Z
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
## 查看软件名
```
adb shell pm list packages -f
adb pull /data/app/com.leon.demo-ZMMnebZlBtlM_xwAxZyXPQ==/base.apk
aapt d badging base.apk
```
# 无线调试
```
adb tcpip 10555
adb connect 10.6.16.126:10555
```
## 安卓11以后无需USB连接
保证设备与电脑连接到同一个局域网，在开发者选项中启用无线调试。在询问要允许在此网络上进行无线调试吗？的对话框中，点击允许。
选择使用配对码配对设备，使用弹窗中的 IP 地址和端口号:
```
adb pair ipaddr:port
提示Enter pairing code: 时输入手机弹窗中的配对码
成功后会显示Successfully paired to ...
connect 命令连接 :
adb connect ipaddr:port
确认连接状态:
adb devices
```