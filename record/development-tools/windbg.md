---
title: Windbg
description: windbg
published: true
date: 2023-10-20T08:27:01.935Z
tags: windows
editor: markdown
dateCreated: 2022-06-22T09:00:07.672Z
---

# 用法
分析还原被破坏的堆栈
https://blog.csdn.net/swartz_lubel/article/details/77920782
https://blog.csdn.net/CJF_iceKing/article/details/119488750

microsoft教程
https://learn.microsoft.com/zh-cn/windows-hardware/drivers/debugger/getting-started-with-windbg

# 环境
 离线系统符号表下载到```c:\symbols```中
```
"C:\Program Files (x86)\Windows Kits\10\Debuggers\x64\symchk.exe" /r "C:\Windows\System32\ntdll.dll" /s SRV*c:\symbols\*http://msdl.microsoft.com/download/symbols -v
```
用symchk导出导入pdb信息
```
"C:\Program Files (x86)\Windows Kits\10\Debuggers\x64\symchk.exe" /om c:\pdb.txt /of "C:\Windows\System32\ntdll.dll"
"C:\Program Files (x86)\Windows Kits\10\Debuggers\x64\symchk.exe" /im "D:\store\pdbinfo\pdb.txt"  /s SRV*c:\symbols\*http://msdl.microsoft.com/download/symbols -v
```
windbg加载离线pdb
```
.sympath+ c:\symbols
.reload
```

# 查看
若要打开或切换到“局部变量”窗口，请在“WinDbg”窗口中的“ 视图 ”菜单上，选择“ 局部变量”。

# 指令
```k```显示堆栈
```bm``` 针对符号下断点，支持匹配表达式。 很多时候你下好几个断点。 比如，把MyClass 所有的成员函数都下断点： bu MyApp!MyClass::*
```g``` 开始运行，```.restart``` 重新运行
```n10``` 以10进制显示值

eg.
```
bm exename!classname::funcname
g
```

