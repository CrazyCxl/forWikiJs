---
title: Ubuntu
description: A quick summary of Ubuntu
published: true
date: 2025-02-14T06:32:49.207Z
tags: 
editor: markdown
dateCreated: 2024-02-08T11:03:27.534Z
---

# 安装
安装过程卡
>禁用网络后再安装

# 配置源
```
sudo vim /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu focal main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu focal-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
```
各版本对应关系
- trusty：Ubuntu 14.04 LTS (Trusty Tahr)
- xenial：Ubuntu 16.04 LTS (Xenial Xerus)
- bionic：Ubuntu 18.04 LTS (Bionic Beaver)
- devel：开发版本，可能对应当前 Ubuntu 开发中的软件包
- Hirsute Ubuntu 21.04 版本的代号，全名为 "Hirsute Hippo"
- impish：Ubuntu 21.10 (Impish Indri)
- groovy：Ubuntu 20.10 (Groovy Gorilla)
- Focal  Ubuntu 20.04 LTS 版本的代号
- Jammy Ubuntu 22.04 LTS （Jammy Jellyfish）


# 常用命令
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

强制安装
apt download xxx
dpkg -i --force-depends ./xxx.deb
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
