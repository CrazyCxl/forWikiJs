---
title: Windbg
description: windbg
published: true
date: 2022-06-22T09:35:41.192Z
tags: windows
editor: markdown
dateCreated: 2022-06-22T09:00:07.672Z
---

# 用法
分析还原被破坏的堆栈
https://blog.csdn.net/swartz_lubel/article/details/77920782
https://blog.csdn.net/CJF_iceKing/article/details/119488750

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
# 指令
```k```显示堆栈