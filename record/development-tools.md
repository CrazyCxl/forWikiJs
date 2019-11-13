---
title: Development Tools
description: for新环境搭建
published: true
date: 2019-11-13T09:37:43.729Z
tags: 
---

# Windows
## 常用工具

- [Bandizip](https://www.bandisoft.com/bandizip/) 解压工具
- [notpad++ ](https://notepad-plus-plus.org/) 文档编辑器*（带有比较插件）*
- [putty](https://www.putty.org/) ssh连接
- [tortoisesvn](https://tortoisesvn.net/downloads.html) SVN
- [git](https://www.git-scm.com/download/) Git官网下载
- [Qt](https://download.qt.io/archive/) qt各个版本的下载地址
- [potplayer](https://potplayer.daum.net/) 视频播放器
- [postman](https://www.getpostman.com/apps) REST调试工具
- [webtorrent](https://webtorrent.io/)
- [FDM](http://www.freedownloadmanager.org/download.htm) 下载工具
- [EagleGet](http://www.eagleget.com/) 下载工具
- [天若OCR截图文字识别](https://pan.baidu.com/s/1IHn8G0ieIWVCH7qVvNdjoQ)
- [dependency](http://www.dependencywalker.com/) dll解析工具
- [matlab](https://blog.csdn.net/josslyn/article/details/79898261)
- [graphviz](http://www.graphviz.org/download/) 可视化工具
- [everything](https://www.voidtools.com/zh-cn/) windows全盘搜索工具
- [WinDirStat](https://windirstat.en.softonic.com/) 磁盘文件分析工具
- [geekuninstaller](https://geekuninstaller.com/download) 卸载工具
- [Rufus](https://rufus.ie/) U盘引导盘制作工具
- [process-explorer](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer) 进程资源管理工具
- snipaste 取色截图工具
- QuickLook

System Or Office下载：https://msdn.itellyou.cn/

## 激活
### 激活专业版
```
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr /skms zh.us.to
slmgr /ato
```

### 激活office 2015
```
cscript ospp.vbs /sethst:vpn.sibogao.cn
cscript ospp.vbs /act
```

### 激活office 2019
```
@echo off
(cd /d "%~dp0")&&(NET FILE||(powershell start-process -FilePath '%0' -verb runas)&&(exit /B)) >NUL 2>&1
title Office 2019 Activator r/Piracy
echo Converting... & mode 40,25
(if exist "%ProgramFiles%\Microsoft Office\Office16\ospp.vbs" cd /d "%ProgramFiles%\Microsoft Office\Office16")&(if exist "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" cd /d "%ProgramFiles(x86)%\Microsoft Office\Office16")&(for /f %%x in ('dir /b ..\root\Licenses16\ProPlus2019VL*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%%x" >nul)&(for /f %%x in ('dir /b ..\root\Licenses16\ProPlus2019VL*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%%x" >nul)
cscript //nologo ospp.vbs /unpkey:6MWKP >nul&cscript //nologo ospp.vbs /inpkey:NMMKJ-6RK4F-KMJVX-8D9MJ-6MWKP >nul&set i=1
:server
if %i%==1 set KMS_Sev=kms7.MSGuides.com
if %i%==2 set KMS_Sev=kms8.MSGuides.com
if %i%==3 set KMS_Sev=kms9.MSGuides.com
cscript //nologo ospp.vbs /sethst:%KMS_Sev% >nul
echo %KMS_Sev% & echo Activating...
cscript //nologo ospp.vbs /act | find /i "successful" && (echo Complete) || (echo Trying another KMS Server & set /a i+=1 & goto server)
pause >nul
exi
```

## 常见问题
### Wireshark 无法发现网卡[^wireshark]

以管理员运行命令行开启npf
>net start npf

#### 启动失败报错“发生系统错误 123 文件名、目录名或卷标语法不正确”

重新安装 [npcap](https://nmap.org/npcap/#download)

关闭npf
>net stop npf

[^wireshark]:https://wiki.wireshark.org/CaptureSetup/CapturePrivileges
