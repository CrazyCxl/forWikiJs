<!-- TITLE: Development Tools -->
<!-- SUBTITLE: for新环境搭建 -->

# Windows
## 激活专业版
```
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr /skms zh.us.to
slmgr /ato
```

## 常用工具

- [Bandizip](https://www.bandisoft.com/bandizip/) 解压工具
- [notpad++ ](https://notepad-plus-plus.org/) 文档编辑器*（带有比较插件）*
- [putty](https://www.putty.org/) ssh连接
- [Qt](https://download.qt.io/archive/) qt各个版本的下载地址
- [potplayer](https://potplayer.daum.net/) 视频播放器
- [postman](https://www.getpostman.com/apps) REST调试工具
- [webtorrent](https://webtorrent.io/)
- [天若OCR截图文字识别](https://pan.baidu.com/s/1IHn8G0ieIWVCH7qVvNdjoQ)
- QuickLook


## 常见问题
### Wireshark 无法发现网卡[^wireshark]

以管理员运行命令行开启npf
>net start npf

关闭npf
>net stop npf

[^wireshark]:https://wiki.wireshark.org/CaptureSetup/CapturePrivileges