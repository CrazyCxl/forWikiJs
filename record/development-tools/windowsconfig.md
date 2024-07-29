---
title: Windows配置
description: 新装系统后的常用配置
published: true
date: 2024-07-29T09:17:16.111Z
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

# 检查
## 查看smb版本

```
#SMB v1 Windows 11/10 和 Windows 8.1
Get-WindowsOptionalFeature –Online –FeatureName SMB1Protocol

#SMB v2 Windows 11/10 和 Windows 8.1
Get-SmbServerConfiguration | Select EnableSMB2Protocol
```

# win11
## 右键菜单栏
### ShellNew
通过注册表regedit查询有哪些
```
计算机\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Discardable\PostSetup\ShellNew
```
查询对应后缀或其子项下的shellnew
```
计算机\HKEY_CLASSES_ROOT\.mdb
```
重命名ShellNew

### BMP 图像
BMP 图像右键删除
- 注册表搜索```ShellNewDisplayName_Bmp```
- 双击然后删除值内容