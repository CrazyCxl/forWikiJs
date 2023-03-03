---
title: Linux
description: A quick summary of Linux
published: true
date: 2023-01-06T08:04:13.939Z
tags: ssh
editor: markdown
dateCreated: 2020-03-19T08:37:41.814Z
---

# 环境搭建
客户端免密ssh登录:https://blog.csdn.net/jeikerxiao/article/details/84105529

```
ssh-keygen -t rsa -b 2048 -C "chenxiaolong"
ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.235.22
```
手动复制客户端id_rsa.pub到服务端authorized_keys中
https://developers.redhat.com/blog/2018/11/02/how-to-manually-copy-ssh-keys-rhel
```
mkdir ~/.ssh/
chmod 700 ~/.ssh  # this is important.
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys  #this is important.
```
# shell
## 管道过滤
输出匹配字符串及之后的内容
```
grep -o "text.*$"
```
输出某一列的内容
```
awk '{ print $2 }'
```

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

