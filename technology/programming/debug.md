---
title: 调试
description: A quick summary of 调试
published: true
date: 2019-11-30T01:44:51.339Z
tags: gdb
---

coredump
===
查看
>coredump list

清除缓存
>rm /var/log/journal/*/*
killall -9 systemd-journald

设置自动清除期限
>journalctl --vacuum-time=2d

gdb
===
查看
---
查看多线程
>info threads

to list "All global and static variable names".
>info variables 

to list "Local variables of current stack frame" (names and values), including static variables in that function.
>info locals

to list "Arguments of the current stack frame" (names and values).
>info args

示例：
```
(gdb) bt
#0  0xfec3c0b5 in _lwp_kill () from /lib/libc.so.1
#1  0xfec36f39 in thr_kill () from /lib/libc.so.1
#2  0xfebe3603 in raise () from /lib/libc.so.1
#3  0xfebc2961 in abort () from /lib/libc.so.1
#4  0xfebc2bef in _assert_c99 () from /lib/libc.so.1
#5  0x08053260 in main (argc=1, argv=0x8047958) at ber.c:480
(gdb) info locals
No symbol table info available.
(gdb) select-frame 5
(gdb) info locals
i = 28
(gdb) 
```
