---
title: vcpkg
description: vcpkg
published: true
date: 2025-03-20T07:22:40.386Z
tags: win
editor: markdown
dateCreated: 2024-02-28T02:55:57.744Z
---

# install
```
 git clone https://github.com/microsoft/vcpkg
 .\vcpkg\bootstrap-vcpkg.bat
 ```

# 使用
在本机使用生成vcpkg.cmake
```
 .\vcpkg\vcpkg integrate install
```

添加定义
```
-DCMAKE_TOOLCHAIN_FILE=D:/develop/vcpkg/vcpkg/scripts/buildsystems/vcpkg.cmake
-DVCPKG_CRT_LINKAGE=static
```

# 常用命令
```
显示已安装
vcpkg list

vcpkg search xxx
vcpkg install xxx
vcpkg remove xxx

#导出
vcpkg export grpc:x64-windows --zip
```
# 注意
安装32位需要指定列如：```opencv:x86-windows```

# 安装grpc
## 下载包
```
export https_proxy=http://127.0.0.1:28081 
 .\vcpkg\vcpkg install grpc:x64-windows
 .\vcpkg\vcpkg install protobuf[zlib] protobuf[zlib]:x64-windows
```
下载失败可以手动下载包放入downloads目录下

## 安装包

>在本机使用生成vcpkg.cmake

在qt cmake使用

添加gprc proto 可执行目录到qt pro 环境 path

```
vcpkg\installed\x64-windows\tools\grpc
vcpkg\installed\x64-windows\tools\protobuf
```
>添加定义


## 使用
```
&"D:\develop\vcpkg\vcpkg\installed\x86-windows\tools\protobuf\protoc.exe" -I .\  --cpp_out=. .\infraredmonitor.proto
&"D:\develop\vcpkg\vcpkg\installed\x64-windows\tools\protobuf\protoc.exe" -I ./ --grpc_out=./ --plugin=protoc-gen-grpc="D:\develop\vcpkg\vcpkg\packages\grpc_x64-windows\tools\grpc\grpc_cpp_plugin.exe" infraredmonitor.proto
```