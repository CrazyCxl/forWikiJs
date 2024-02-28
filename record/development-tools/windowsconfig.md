---
title: Windows配置
description: 新装系统后的常用配置
published: true
date: 2024-02-28T01:48:20.547Z
tags: win
editor: markdown
dateCreated: 2024-02-28T01:45:52.116Z
---

# 系统优化
## 关闭热门搜索框
管理员cmd中运行
```
reg add HKCU\Software\Policies\Microsoft\Windows\explorer /v DisableSearchBoxSuggestions /t reg_dword /d 1 /f11
```

## 使用全屏开始菜单
个性化->开始->使用全屏“开始”屏幕