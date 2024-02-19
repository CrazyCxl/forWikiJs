---
title: Development Tools
description: for新环境搭建
published: true
date: 2024-02-19T06:07:02.825Z
tags: 
editor: markdown
dateCreated: 2024-02-08T11:00:58.708Z
---

# Android
## 常用apk
- [指南针](https://pan.baidu.com/s/13gVS9bor5pjIQG2pZluS_Q?pwd=lwfy) 方位海拔查看
- v2rayNG
- tvbox
- firfox

# Windows
System Or Office下载：https://msdn.itellyou.cn/

## 常用工具

- [7zip](https://www.7-zip.org/) 解压工具
- [notpad3](https://www.rizonesoft.com/downloads/notepad3/) 文档编辑器
- [potplayer](https://potplayer.daum.net/) 视频播放器
- [postman](https://www.getpostman.com/apps) REST调试工具
- [NDM](https://neatdownloadmanager.com/index.php/en/) 下载工具
- [autohotkey](https://www.autohotkey.com/) 快捷键脚本
- [everything](https://www.voidtools.com/zh-cn/) windows全盘搜索工具
- [geekuninstaller](https://geekuninstaller.com/download) 卸载工具
- [Rufus](https://rufus.ie/) U盘引导盘制作工具
- [screentogif](https://www.screentogif.com/) GIF 制作工具
- [recuva](https://www.ccleaner.com/zh-cn/recuva) 恢复软件
- [goldendict](https://github.com/xiaoyifang/goldendict/releases) 翻译工具 词典[freemdict](https://forum.freemdict.com/)
- [localsend](https://github.com/localsend/localsend/releases) 局域网传输工具
- [womic](https://wolicheng.com/womic/download.html) 手机麦克风
- [Office Tool plus](https://otp.landian.vip/zh-cn/) office破解
- [goodsync](https://www.goodsync.com/) 本地目录同步
- snipaste 取色截图工具
- QuickLook

## 测试工具
- [mouseteseter](https://github.com/microe1/MouseTester/releases) 鼠标cpi测试
- [WinDirStat](https://windirstat.en.softonic.com/) 磁盘文件分析工具
- [crystaldiskinfo](https://crystalmark.info/en/software/crystaldiskinfo/) 硬盘状态查询
- [process-explorer](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer) 进程资源管理工具
- [CoreTemp](https://www.alcpu.com/CoreTemp/) cpu温度显示

## 编码工具
- [understand](https://licensing.scitools.com/download) 代码分析工具
- [sqlitebrowser](https://sqlitebrowser.org/dl/) sql数据查看工具
- [Qt](https://download.qt.io/archive/) qt各个版本的下载地址
- [putty](https://www.putty.org/) ssh连接
- [tortoisesvn](https://tortoisesvn.net/downloads.html) SVN
- [git](https://www.git-scm.com/download/) Git官网下载
- [dependency](http://www.dependencywalker.com/) dll解析工具
- [graphviz](http://www.graphviz.org/download/) 可视化工具

# chrome 配置
### 开启并行下载支持
打开`chrome://flags/`
搜索`Parallel downloading`并设为`enabled`

# Linux
### 常用工具
fail2ban 安全防护

# 常见问题
### Wireshark 无法发现网卡[^wireshark]

以管理员运行命令行开启npf
>net start npf

#### 启动失败报错“发生系统错误 123 文件名、目录名或卷标语法不正确”

重新安装 [npcap](https://nmap.org/npcap/#download)

关闭npf
>net stop npf

[^wireshark]:https://wiki.wireshark.org/CaptureSetup/CapturePrivileges
