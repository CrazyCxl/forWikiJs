<!-- TITLE: Development Tools -->
<!-- SUBTITLE: for新环境搭建 -->

# Windows
## 常用工具

- [Bandizip](https://www.bandisoft.com/bandizip/) 解压工具
- [notpad++ ](https://notepad-plus-plus.org/) 文档编辑器*（带有比较插件）*
- [putty](https://www.putty.org/) ssh连接
- [Qt](https://download.qt.io/archive/) qt各个版本的下载地址

## 常见问题
### Wireshark 无法发现网卡[^wireshark]

以管理员运行命令行开启npf
>net start npf

关闭npf
>net stop npf

[^wireshark]:https://wiki.wireshark.org/CaptureSetup/CapturePrivileges