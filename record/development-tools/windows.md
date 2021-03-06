---
title: Windows
description: Windows 下的编程问题
published: true
date: 2021-03-17T01:48:54.052Z
tags: 
---

# 右键菜单栏
右键菜单栏添加vs code 打开 https://www.jianshu.com/p/e8c29211fba9

# 快捷键
## 查看快捷键占用
参考：
https://www.zhihu.com/question/21020398/answer/1191762268

使用spyxx.exe
消息监听WM_HOTKEY
然后查看属性

## Win + R
### 打开启动项目录
> shell:startup

# Powershell
## 查看历史
>(Get-PSReadlineOption).HistorySavePath
cat (Get-PSReadlineOption).HistorySavePath

## 查看文件md5
certutil -hashfile .\libtest.1.dylib md5
Get-Filehash -Path .\libtest.a -Algorithm MD5

## 转化为utf8编码的窗口
chcp 65001

# 创建FTP
https://blog.csdn.net/qq_34610293/article/details/79210539

# VS 相关
## 使用 **Microsoft Visual Studio 2017 Installer Projects** 打包时卡在正在准备安装这一步

环境Win10 vs2017 vs2013

通过事件日志可以看出缺少 ```C:\Windows\Microsoft.NET\Framework\URTInstallPath_GAC``` 目录，创建该目录即可

## 创建CLR项目
https://www.red-gate.com/simple-talk/dotnet/net-development/creating-ccli-wrapper/

# NSIS打包工具
官网：http://nsis.sourceforge.net/Main_Page

# 库相关
## DLL库信息与依赖查看

dependencywalker 工具：http://www.dependencywalker.com/

或者使用vs自带的工具[^vs_dll_tool]
```
查看lib信息
dumpbin   /LINKERMEMBER   *.lib   >   1.txt

查看dll信息
dumpbin   /EXPORTS  *.dll  >1.txt

查看是32还是64位
dumpbin   /HEADERS  filename
```

查看函数声明
```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation 1981-2000. All rights reserved.Undecoration
of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## 根据dll生成lib

- dumpbin   /EXPORTS  *.dll  >1.txt
- 复制1.txt中的函数名称到1.def
- 添加EXPORTS到1.def第一行
- lib /def:1.def /out:yourfile.lib


## Qt使用QLibary加载dll库失败[^dll_error]

使用 `SetDllDirectory`[^dll_lib] 后再加载

## Q&A

Q: vs运行qt程序时相对路径访问失败
>vs 默认当前目录为工程目录，而不是可自行程序所在的目录

Q: qt开启调试失败
>下载[wdk](https://docs.microsoft.com/en-us/windows-hardware/drivers/download-the-wdk) *( Windows Driver Kit )* 

Q: 调用dll中的函数后发生堆栈溢出或非法访问等错误
>可以是dll是win api方式打包成的（用dumpbin工具查看dll中是否有@4类似的参数字节数提示），此时需要在头文件中声明函数为 **_stdcall** 调用协议

[^dll_error]:https://stackoverflow.com/questions/22354639/loading-library-with-dependency-with-qlibrary
[^dll_lib]:https://msdn.microsoft.com/en-us/library/ms686203%28VS.85%29.aspx
[^vs_dll_tool]:https://blog.csdn.net/linuxheik/article/details/80494846
