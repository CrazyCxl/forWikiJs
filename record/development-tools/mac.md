<!-- TITLE: Mac -->
<!-- SUBTITLE: A quick summary of Mac -->

# 使用nm命令解析符号表
>nm path/xxx.a

# 发布Qt程序
参考：http://doc.qt.io/qt-5/osx-deployment.html

## 依赖问题

可以在库项目的pro文件中通过`QMAKE_LFLAGS_SONAME  = -Wl,-install_name,@executable_path/../Frameworks/`来配置库文件存放位置

然后在app项目的pro文件中通过`QMAKE_BUNDLE_DATA`来将库依赖复制到对应位置

示例：
```
    MY.path = Contents/Frameworks
    MY.files = ../libmyapp/libmyapp.1.dylib
    QMAKE_BUNDLE_DATA += MY
```

## macdeployqt

macdeployqt 可以自动向app中补充所需的依赖文件

通过-dmg参数可以直接生产dmg文件

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

## 运行程序时报错`dyld: Library not loaded:Reason: image not found`

这是由于依赖的库文件没找到，可以通过`otool -L `命令来查看程序所需的依赖库列表

可以通过设置`DYLD_LIBRARY_PATH`宏 * ( Projects > Run (under something like Qt 4.8.5) > Run Environment > Add ) * 来设置运行时需要的依赖目录

也可以在app编译之前通过install_name_tool来配置库文件的位置

示例
```
install_name_tool -id @executable_path/../Frameworks/QtCore.framework/Versions/4.0/QtCore  plugandpaint.app/Contents/Frameworks/QtCore.framework/Versions/4.0/QtCore
```



[^xcode_path]:该路径为你的xcode安装路径
[^macos]:该值为mac系统版本号
[^macgcc]:该值为mac的编译工具版本号，可通过 `clang -v` 命令来获取
