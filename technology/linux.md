---
title: Linux
description: A quick summary of Linux
published: true
date: 2020-02-17T07:52:31.447Z
tags: 
---

# Debian
## 换源
- 打开界面software工具
- 全部勾选从网络中下载
- 切换为中国源
- 命令行中运行apt update

# 常用命令
## 时间戳
date +%s
date -d @\`date +%s`

## 查看符号表
nm 命令
```nm *.a```