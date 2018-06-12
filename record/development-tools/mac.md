<!-- TITLE: Mac -->
<!-- SUBTITLE: A quick summary of Mac -->

# 常见问题
## qt打开项目报错 `qt could not resolve sdk path for macosx`
### 确保已安装xcode

- 在App Store中安装
- 去网站下对应的dmg包：https://developer.apple.com/download/more/

安装完成后运行
>sudo xcode-select -s /Applications/Xcode.app/Contents/Developer [^xcode_path]

### 查看qt配置是否正确

在qt安装目录中搜索并打开`qdevice.pri`文件
>!host_build:QMAKE_MAC_SDK = macosx10.8 [^macos]
>GCC_MACHINE_DUMP = x86_64-apple-darwin15.0.0 [^macgcc]

[^xcode_path]:该路径为你的xcode安装路径
[^macos]:该值为mac系统版本号
[^macgcc]:该值为mac的编译工具版本号，可通过 `clang -v` 命令来获取
