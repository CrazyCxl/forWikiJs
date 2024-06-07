---
title: Flutter
description: 
published: true
date: 2024-06-07T08:29:27.361Z
tags: 
editor: markdown
dateCreated: 2024-05-28T06:53:51.914Z
---

# 环境搭建
参考：https://zhuanlan.zhihu.com/p/480002331

## 问题
Android license status unknown
>flutter doctor --android-licenses 

HTTP Host Availability

>打开/path-to-flutter-sdk/packages/flutter_tools/lib/src/http_host_validator.dart文件，修改https://maven.google.com/为 google maven 的国内镜像，如https://maven.aliyun.com/repository/google/
删除/path-to-flutter-sdk/bin/cache 文件夹
重新执行flutter doctor

## 注意
- 在vscode 中启动并连接Android虚拟机

# 翻译
参考1：https://docs.flutter.dev/ui/accessibility-and-internationalization/internationalization
参考2：https://zhuanlan.zhihu.com/p/688095179
（cxl）参考3：https://zhuanlan.zhihu.com/p/702234616