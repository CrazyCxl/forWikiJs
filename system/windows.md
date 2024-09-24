---
title: Windows
description: Windows 下的编程问题
published: true
date: 2024-09-24T07:24:17.127Z
tags: 
editor: markdown
dateCreated: 2024-02-08T11:02:37.295Z
---

# 文件资源管理器
## 右键菜单栏
右键菜单栏添加vs code 打开 https://www.jianshu.com/p/e8c29211fba9

## 查找指定文件内容
在右上角的搜索框中输入文件后缀和搜索关键字
```
*.txt example
```

## Win + R 打开启动项目录
> shell:startup

# 快捷键
## 查看快捷键占用
参考：
https://stackoverflow.com/questions/829007/find-out-what-process-registered-a-global-hotkey-windows-api

使用spyxx.exe
选择`监视`-`日志消息`
选中`系统中所有窗口`
切换到`消息`界面
点击`全部清除`
消息监听WM_HOTKEY
然后查看属性



# Powershell
## 查看历史
>(Get-PSReadlineOption).HistorySavePath
cat (Get-PSReadlineOption).HistorySavePath

## 查看文件md5
certutil -hashfile .\libtest.1.dylib md5
Get-Filehash -Path .\libtest.a -Algorithm MD5


# 睡眠模式
https://www.zhihu.com/question/264893048
查看阻止睡眠模式的程序
```
powercfg /requests
```

# NSIS打包工具
官网：http://nsis.sourceforge.net/Main_Page

# NSSM 服务创建
To hide the terminal window when running V2Ray on Windows, you can use a utility called "nssm" (Non-Sucking Service Manager) to create a Windows service for V2Ray. Here's how you can do it:

- Download the nssm utility from the official website: https://nssm.cc/download
- Extract the downloaded archive and locate the nssm.exe file.
- Open Command Prompt or PowerShell as an ```administrator```
- Navigate to the directory where nssm.exe is located.
- Run the following command to create a new service:
```
nssm install V2RayService
```
In the nssm Service Installer window that appears, specify the following:

>Path: Browse and select the V2Ray executable (e.g., v2ray.exe).
>Startup directory: Specify the directory where V2Ray is installed.
>Arguments: Enter any necessary command-line arguments for V2Ray.

Click the "Install service" button to create the service.
Once the service is created, you can start it by running the following command:
```
nssm start V2RayService
```

## 查看nssm创建的服务列表
```
Get-WmiObject win32_service | ?{$_.PathName -like '*nssm*'} | select Name, DisplayName, State, PathName
```


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

查看编译器版本
dumpbin /all xxx.lib | findstr _MSC_VER
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
