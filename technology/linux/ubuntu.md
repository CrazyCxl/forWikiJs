---
title: Ubuntu
description: A quick summary of Ubuntu
published: true
date: 2021-04-20T08:29:54.698Z
tags: 
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
deb包与rpm包互转
---
参考：https://www.tecmint.com/convert-from-rpm-to-deb-and-deb-to-rpm-package-using-alien/