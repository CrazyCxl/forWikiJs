---
title: Linux
description: A quick summary of Linux
published: true
date: 2024-11-11T09:43:04.886Z
tags: ssh
editor: markdown
dateCreated: 2024-02-08T11:01:12.705Z
---

# 环境搭建
客户端免密ssh登录:https://blog.csdn.net/jeikerxiao/article/details/84105529

```
ssh-keygen -t rsa -b 2048 -C "chenxiaolong"
ssh-copy-id  root@192.168.235.22
ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.235.22
```
手动复制客户端id_rsa.pub到服务端authorized_keys中
https://developers.redhat.com/blog/2018/11/02/how-to-manually-copy-ssh-keys-rhel
```
mkdir ~/.ssh/
chmod 700 ~/.ssh  # this is important.
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys  #this is important.
```

## 创建用户
```
useradd cxl
#密码无效也继续
passwd cxl
/etc/sudoers 文件里添加cxl管理员权限
	cxl ALL=(ALL) ALL
```

更改目录所有者
```
chown cxl:cxl -R dir
chown cxl -R dir
chgrp cxl -R dir
```

## 环境变量
/etc/environment

# shell
## 管道过滤
输出匹配字符串及之后的内容
```
grep -o "text.*$"
```
输出某一列的内容
```
awk '{ print $2 }'
```

# 库与依赖
## 查看符号表

nm 命令
```
nm -D libName.so | grep symbel symbolName
#使用c++filt查看函数名称
echo "_ZN3Ice60Object12ice_dispatchERNS_7RequestESt8functionIFbvEES3_IFb..." | c++filt
```

## RUNPATH 与RPATH
- RUNPATH 是直接运行依赖库路径
- RPATH   是所有依赖路径

ldd 有依赖，但 readelf -d 查看NEEDED没有包含代表不是直接依赖，需要设置RPATH（```-Wl,--disable-new-dtags```）

## 查看和修改运行依赖
查看
```
ldd path
readelf -d <path-to-elf> 
```
[patchelf](https://github.com/NixOS/patchelf) 修改NEEDED
```
patchelf --replace-needed ../libsomething1.so /foo/bar/libsomething1.so mysharedobject.so
```

rpath
```
#重设
patchelf --set-rpath '/home/gpsdk/newlib/:/home/gpsdk/threads/lib/' app
#添加
patchelf --add-rpath '/home/gpsdk/newlib/:/home/gpsdk/threads/lib/' app
```

## 修改静态库中的函数名称
```
#分解为.o文件
ar x ../libcustom.a

#修改.o文件中的函数名称
objcopy --redefine-sym custom_function=new_custom_function custom_lib.o

#重新打包为静态库
ar rcs libcustom_modified.a *.o

#测试使用
c++ main.cpp -L. -lcustom_modified
```

# 通用命令
## 重定向
- stdin 0
- stdout 1
- stderr 2
- null /dev/null

## 速度测试
```
# 计算磁盘速度
dd if=/dev/sda1 of=/dev/null bs=800M count=10
# 计算内存拷贝速度
dd if=/dev/zero of=/dev/null bs=1G count=10
```

## 时间戳
```
date +%s
date -d @\`date +%s`
```

## makeself 自解压打包
可以在里面套个压缩包，脚本里解压到指定目录
```
添加脚本
#!/bin/bash tar zxpf nginx.tgz -C /tmp/ cd /tmp/nginx ./configure --prefix=/tmp/nginxtest make make install

运行命令
makeself --nocomp --needroot nginx nginx.bin nginx ./init.sh
```

# 文件
## 权限
**r=4  w=2  x=1**

- rwx 4+2+1=7
- rw- 4+2=6
- r-x 4+1=5

**umask**

- 跟3位或 `4位（第一位必须为0，表示八进制 ）`数字来设置默认权限
- 不加参数表示获取默认权限

创建并格式化分区
===
创建
---
>\$ fdisk -l
>$ fdisk /dev/sdb
命令(输入 m 获取帮助)：m

输入n创建分区（一直默认，选primary）
创建完成后输入w保存并退出

格式化
---
创建成功后输入以下命令来格式化
>$ mkfs.ext4 /dev/sdb1

开机自动挂载
---
参考[arch wiki](https://wiki.archlinux.org/index.php/Fstab_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
>$ vi /etc/fstab

输入
> /dev/sdb1 /dir ext4 defaults 0 2

# 性能分析
```
#录所有cpu调用
sudo perf record -e cycles -g -- xxx
sudo perf report
```
使用+号展开堆栈
perf record -e cycles -g 是用来记录程序运行期间 CPU cycles 事件的性能数据，并生成调用图（call graph）。下面是对每个参数的解释：

- perf record: 启动 perf 记录程序的性能事件。
- -e cycles: 指定要记录的性能事件为 CPU cycles。cycles 事件表示 CPU 执行的时钟周期数，这是一个通用的性能计数器，用于衡量程序的 CPU 使用情况。
- -g: 启用调用图记录。这会捕获程序执行时的调用栈信息，帮助你分析函数调用关系，找出性能瓶颈。