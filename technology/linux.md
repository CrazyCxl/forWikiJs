---
title: Linux
description: A quick summary of Linux
published: true
date: 2020-11-20T08:49:41.167Z
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

## 基础软件安装
```
apt install zsh git net-tools
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

# 通用命令
## 时间戳
date +%s
date -d @\`date +%s`

## 库相关
### 查看符号表
nm 命令
```
nm -D libName.so | grep symbel symbolName
```
### 查看和修改运行依赖
查看
```
ldd path
readelf -d <path-to-elf> 
```
[patchelf](https://github.com/NixOS/patchelf) 修改NEEDED
```
patchelf --replace-needed ../libsomething1.so /foo/bar/libsomething1.so mysharedobject.so
```

