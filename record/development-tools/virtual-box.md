---
title: Virtual Box
description: A quick summary of Virtual Box
published: true
date: 2024-01-30T08:41:11.664Z
tags: 
editor: markdown
dateCreated: 2020-03-19T08:37:50.584Z
---

# 下载与安装
https://www.virtualbox.org/wiki/Downloads

# 虚拟机

- Windows 下创建 Mac 虚拟机：https://blog.csdn.net/chy555chy/article/details/51407410


# 常见问题
Q: 安装增强功能后启动虚拟机黑屏
>显存开到最大

Q: Win10安装虚拟机后无法ping通？
>配置Win10防火墙允许ICMP [^ping]

Q: 如何进入Mac虚拟机的recovery模式
>按F12进boot shell，输入`FS2:`后再输入`cd com.apple.recovery.boot`，之后就可以输入`boot.efi`进入Recovery了[^mac_recovery]


[^ping]:https://kb.iu.edu/d/aopy
[^mac_recovery]:http://anadoxin.org/blog/disabling-system-integrity-protection-from-guest-el-capitan-under-virtualbox-5.html