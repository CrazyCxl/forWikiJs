---
title: Nmap
description: network tool nmap
published: true
date: 2026-01-28T07:23:15.467Z
tags: nmap
editor: markdown
dateCreated: 2024-02-08T11:04:11.739Z
---

# 常用命令
扫描IP段
```
nmap -sP 192.168.200.*
nmap -sP 192.168.200.100-200
```

# ncat
监听tcp并接收数据
```
ncat -l 12345 > recv.bin
```
发送tcp
```
ncat ip port < file.bin
```
连接tcp并接收数据
```
ncat ip port > file.bin
```
