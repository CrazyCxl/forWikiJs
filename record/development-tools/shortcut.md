---
title: shortcut
description: hot key in software
published: true
date: 2022-08-03T09:08:40.439Z
tags: 
editor: markdown
dateCreated: 2022-08-03T09:08:40.439Z
---

# Chrome
## 依赖
- vimium

## 常用快捷键
ctrl+t 打开新标签页
ctrl+w 关闭标签页
F6 回到地址栏
f 快捷操作
K 转到右边标签页
J 转到左边标签页

# Autohotkey
下载：https://www.autohotkey.com/

## 用法
设置matlab快捷删除行
```
#IfWinActive,ahk_exe MATLAB.exe
    ^d::send,{End}{Home 2}+{Down}{Del}
#IfWinActive
```