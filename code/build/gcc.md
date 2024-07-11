---
title: GCC
description: for gcc c++
published: true
date: 2024-07-11T02:19:49.959Z
tags: 
editor: markdown
dateCreated: 2024-07-11T02:19:49.959Z
---

# 宏
```
//指定版本
int foo() __attribute__ ((symver ("foo@VERSION_1.0"))) 
//指定可见性
__attribute__ ((visibility ("default")));
```
有些版本需要指定可见性，可以直接用可见性替换版本来不指定版本，方便编译
