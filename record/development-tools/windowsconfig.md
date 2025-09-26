---
title: Windows配置
description: 新装系统后的常用配置
published: true
date: 2025-09-26T01:10:37.815Z
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
## 配置取消更新
运行，regedit，回车，打开注册表编辑器。然后打开这个注册表路径
```HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings```
在空白处鼠标右键新建DWORD值，名称是```FlightSettingsMaxPauseDays```

双击这个FlightSettingsMaxPauseDays，修改里面的值为任意比较大的数字（理论上不超过十进制的4294967295都可以，最好别超过十进制的100000，多了也没用），例如十进制的10000，代表可以设置为1万天后继续更新。

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

# chrome
新版去掉不安全的下载：https://blog.csdn.net/Menwe1/article/details/135114546
- 打开浏览器设置页面，点击 隐私和安全，进入 网站设置页面
- 点击 更多内容设置，展开后点击不安全内容
-  在允许不安全内容添加网址

## 安全的dns
```
https://doh.pub/dns-query
https://dns.alidns.com/dns-query
```

## 这些扩展程序不再受支持，因此已停用
快捷方式目标里加：
```
--disable-features=ExtensionManifestV2Unsupported,ExtensionManifestV2Disabled
```