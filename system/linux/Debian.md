---
title: Debian
description: debian linux
published: true
date: 2024-02-27T02:42:08.521Z
tags: 
editor: markdown
dateCreated: 2024-02-27T02:42:08.521Z
---

# install
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
