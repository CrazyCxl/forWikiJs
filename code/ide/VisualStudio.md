---
title: Msvc
description: A quick summary of Msvc
published: true
date: 2024-02-27T03:06:03.233Z
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
<table border="1" width="700" cellspacing="1" cellpadding="1" style="color:rgb(69,69,69);font-family:'PingFang SC', 'Microsoft YaHei', SimHei, Arial, SimSun;font-size:16px;"><tbody><tr><td>名字</td>
<td>版本号</td>
<td>简称</td>
<td>全称</td>
</tr><tr><td>msvc70</td>
<td>VC7.0</td>
<td>VS2002</td>
<td>Microsoft Visual Studio <strong>2002</strong></td>
</tr><tr><td>msvc71</td>
<td>VC7.1</td>
<td>VS2003</td>
<td>Microsoft Visual Studio <strong>2003</strong></td>
</tr><tr><td>msvc80</td>
<td>VC8.0</td>
<td>VS2005</td>
<td>Microsoft Visual Studio <strong>2005</strong></td>
</tr><tr><td>msvc90</td>
<td>VC9.0</td>
<td>VS2008</td>
<td>Microsoft Visual Studio <strong>2008</strong></td>
</tr><tr><td> </td>
<td>VC10.0</td>
<td>VS2010</td>
<td>Microsoft Visual Studio <strong>2010</strong></td>
</tr><tr><td> </td>
<td>VC11.0</td>
<td>VS2012</td>
<td>Microsoft Visual Studio <strong>2012</strong></td>
</tr><tr><td> </td>
<td>VC12.0</td>
<td>VS2013</td>
<td>Microsoft Visual Studio <strong>2013</strong></td>
</tr><tr><td> </td>
<td>VC13.0</td>
<td>VS2014</td>
<td>Microsoft Visual Studio <strong>2014</strong></td>
</tr><tr><td> </td>
<td>VC14.0</td>
<td>VS2015</td>
<td>Microsoft Visual Studio <strong>2015</strong></td>
</tr><tr><td> </td>
<td> </td>
<td> </td>
<td> </td>
</tr><tr><td> </td>
<td> </td>
<td> </td>
<td> </td>
</tr></tbody></table>