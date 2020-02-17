---
title: Linux
description: A quick summary of Linux
published: true
date: 2020-02-17T08:02:33.835Z
tags: 
---

# Debian
## 换源
- 打开界面software工具
- 全部勾选从网络中下载
- 切换为中国源
- 命令行中运行apt update

## 安装VirtualBox增强功能
>apt-get install build-essential module-assistant
>m-a prepare
>sh /media/cdrom/VBoxLinuxAdditions.run

# 通用命令
## 时间戳
date +%s
date -d @\`date +%s`

## 查看符号表
nm 命令
```nm *.a```