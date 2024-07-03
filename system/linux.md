---
title: Linux
description: A quick summary of Linux
published: true
date: 2024-07-03T03:36:42.353Z
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

# 通用命令
## 计算磁盘速度
```
dd if=/dev/sda1 of=/dev/null bs=800M count=10
```

## 时间戳
date +%s
date -d @\`date +%s`

## 库相关
### 查看符号表

nm 命令
```
nm -D libName.so | grep symbel symbolName
#使用c++filt查看函数名称
echo "_ZN3Ice60Object12ice_dispatchERNS_7RequestESt8functionIFbvEES3_IFb..." | c++filt
```
### 查看和修改运行依赖
查看
```
ldd path
readelf -d <path-to-elf> 
```
[patchelf](https://github.com/NixOS/patchelf) 修改NEEDED
```
patchelf --replace-needed ../libsomething1.so /foo/bar/libsomething1.so mysharedobject.so
```

重设rpath
```
patchelf --set-rpath '/home/gpsdk/newlib/:/home/gpsdk/threads/lib/' app
```

### 修改静态库中的函数名称
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

# 重定向
- stdin 0
- stdout 1
- stderr 2
- null /dev/null

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
