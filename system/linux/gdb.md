---
title: debug
description: A quick summary of 调试
published: true
date: 2024-07-17T01:29:53.451Z
tags: gdb
editor: markdown
dateCreated: 2024-02-08T11:03:09.056Z
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

# gdb
# 常用
```
# 启用日志记录并指定日志文件名
set logging on
set logging file mappings.log

# 获取进程的内存映射信息
info proc mappings

# 关闭日志记录
set logging off

# 启用历史
set history save on
set history filename ~/.gdb_history
set history size 1000

列出断点
info b
查看数组20个元素
p *arr@20
x/20x 0x7f7e00000000
```

多线程
---
- info threads
- thread num

查看内存
---
参考：https://blog.csdn.net/ztguang/article/details/51015760
```
x/ (n,f,u为可选参数)
- n 需要显示的内存单元个数
- f 显示格式
               x(hex) 按十六进制格式显示变量。
               d(decimal) 按十进制格式显示变量。
               u(unsigned decimal) 按十进制格式显示无符号整型。
               o(octal) 按八进制格式显示变量。
               t(binary) 按二进制格式显示变量。
               a(address) 按十六进制格式显示变量。
               c(char) 按字符格式显示变量。
               f(float) 按浮点数格式显示变量
- u：每个单元的大小，按字节数来计算。默认是4 bytes。GDB会从指定内存地址开始读取指定字节，并把其当作一个值取出来，并使用格式f来显示
               b:1 byte
               h:2 bytes
               w:4 bytes
               g:8 bytes
```

以十六进制显示100个byte：
>x/100xb address

变量
---
- info variables 
- info locals
- info args

追踪显示变量a
display a

设置自动输出地址值
set print address on

设置每个数组元素占一行
set print array on

设置数组显示长度
set print elements

按行显示结构体
set print pretty on

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

查看segment fault地址
---
```
(gdb) p $_siginfo._sifields._sigfault.si_addr
```