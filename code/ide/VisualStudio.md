---
title: Msvc
description: A quick summary of Msvc
published: true
date: 2024-03-04T01:17:27.131Z
tags: 
editor: markdown
dateCreated: 2024-02-08T11:02:04.064Z
---

# VS 相关
## 插件推荐
- [注释工具doxygen](https://marketplace.visualstudio.com/items?itemName=FinnGegenmantel.doxygenComments)

双击或使用vs bin目录下的 VSIXInstaller.exe 安装下载好的插件文件

## 使用 **Microsoft Visual Studio 2017 Installer Projects** 打包时卡在正在准备安装这一步

环境Win10 vs2017 vs2013

通过事件日志可以看出缺少 ```C:\Windows\Microsoft.NET\Framework\URTInstallPath_GAC``` 目录，创建该目录即可

## 远程调试win7程序时报错：“远程操作花费的时间比预期要长”
参考：https://stackoverflow.com/questions/12252969/visual-studio-2012-a-remote-operation-is-taking-longer-than-expected
管理员运行cmd
```
netsh winsock reset catalog
netsh int ip reset reset.log hit
```

## 创建CLR项目
https://www.red-gate.com/simple-talk/dotnet/net-development/creating-ccli-wrapper/

## 调试内存泄漏工具
appverif
win7、2008 版下载：https://www.microsoft.com/en-us/download/details.aspx?id=8442

# 版本对应关系
![img](https://i.imgur.com/00GKVuO.png)