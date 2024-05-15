---
title: Linux
description: A quick summary of Linux
published: true
date: 2024-05-15T07:56:22.411Z
tags: ssh
editor: markdown
dateCreated: 2024-02-08T11:01:12.705Z
---

# 环境搭建
客户端免密ssh登录:https://blog.csdn.net/jeikerxiao/article/details/84105529

```
ssh-keygen -t rsa -b 2048 -C "chenxiaolong"
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
time dd if=/dev/sda1 of=/dev/null bs=800M count=10
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

输入n创建分区
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
> /dev/sdb1 /dir ext4 defaults 1 2
