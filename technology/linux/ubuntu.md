---
title: Ubuntu
description: A quick summary of Ubuntu
published: true
date: 2024-01-30T08:22:43.193Z
tags: 
editor: markdown
dateCreated: 2020-03-19T08:38:08.233Z
---

常用命令
===
apt相关
---
### 查询类
```
查找安装包
apt-cache search keyword
查看版本与来源
apt-cache policy keyword

列出包文件列表
apt-file list name
dpkg -L name

列出已安装软件列表
dpkg -l

搜索文件所在安装包
dpkg -S /path/to/file
```

### 包冲突导致的安装失败（unmet）
使用aptitude工具来安装，过程中输入n来选择方案
```
$ sudo apt-get install aptitude
$ sudo aptitude install package-name
```
deb包与rpm包互转
---
参考：https://www.tecmint.com/convert-from-rpm-to-deb-and-deb-to-rpm-package-using-alien/