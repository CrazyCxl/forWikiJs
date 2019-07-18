<!-- TITLE: Development Tools -->
<!-- SUBTITLE: for新环境搭建 -->

# Windows
## 激活专业版
```
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr /skms zh.us.to
slmgr /ato
```

## 激活office 2015
```
cscript ospp.vbs /sethst:vpn.sibogao.cn
cscript ospp.vbs /act
```

## 常用工具

- [Bandizip](https://www.bandisoft.com/bandizip/) 解压工具
- [notpad++ ](https://notepad-plus-plus.org/) 文档编辑器*（带有比较插件）*
- [putty](https://www.putty.org/) ssh连接
- [Qt](https://download.qt.io/archive/) qt各个版本的下载地址
- [potplayer](https://potplayer.daum.net/) 视频播放器
- [postman](https://www.getpostman.com/apps) REST调试工具
- [webtorrent](https://webtorrent.io/)
- [FDM](http://www.freedownloadmanager.org/download.htm) 下载工具
- [天若OCR截图文字识别](https://pan.baidu.com/s/1IHn8G0ieIWVCH7qVvNdjoQ)
- [dependency](http://www.dependencywalker.com/) dll解析工具
- [matlab](https://blog.csdn.net/josslyn/article/details/79898261)
- [graphviz](http://www.graphviz.org/download/) 可视化工具
- [everything](https://www.voidtools.com/zh-cn/) windows全盘搜索工具
- [WinDirStat](https://windirstat.en.softonic.com/) 磁盘文件分析工具
- [geekuninstaller](https://geekuninstaller.com/download) 卸载工具
- [Rufus](https://rufus.ie/) U盘引导盘制作工具
- snipaste 取色截图工具
- QuickLook

System Or Office下载：https://msdn.itellyou.cn/

## 常见问题
### Wireshark 无法发现网卡[^wireshark]

以管理员运行命令行开启npf
>net start npf

#### 启动失败报错“发生系统错误 123 文件名、目录名或卷标语法不正确”

重新安装 [npcap](https://nmap.org/npcap/#download)

关闭npf
>net stop npf

[^wireshark]:https://wiki.wireshark.org/CaptureSetup/CapturePrivileges
