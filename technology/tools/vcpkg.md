---
title: vcpkg
description: for vcpkg
published: true
date: 2023-06-12T06:42:51.477Z
tags: windows, vcpkg
editor: markdown
dateCreated: 2023-06-12T06:42:51.477Z
---

# 安装
```
git clone https://github.com/microsoft/vcpkg
.\vcpkg\bootstrap-vcpkg.bat
```

# 常用命令
## 包下载
```
export https_proxy=http://127.0.0.1:28081 
.\vcpkg\vcpkg install grpc:x64-windows
.\vcpkg\vcpkg install protobuf[zlib] protobuf[zlib]:x64-windows
```
下载失败可以手动下载包放入downloads目录下

## 安装
生成vcpkg.cmake
.\vcpkg\vcpkg integrate install

## 使用
### Qt中使用
添加gprc proto 可执行目录到qt pro 环境 path
```
vcpkg\installed\x64-windows\tools\grpc
vcpkg\installed\x64-windows\tools\protobuf
```
设置cmake变量
```
-DCMAKE_TOOLCHAIN_FILE=D:/develop/vcpkg/vcpkg/scripts/buildsystems/vcpkg.cmake
-DVCPKG_CRT_LINKAGE=static

```

## 其他
查看已安装
```
vcpkg list
```
