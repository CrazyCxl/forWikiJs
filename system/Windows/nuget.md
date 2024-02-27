---
title: Nuget
description: nuget in linux or windows
published: true
date: 2023-03-15T02:22:44.318Z
tags: nuget
editor: markdown
dateCreated: 2022-11-24T01:51:29.460Z
---

# 常用命令
## 源管理
```
nuget sources list
nuget sources add -name cxl -source http://xxx/index.json
nuget sources enable -name cxl
nuget sources disable -name cxl2
```

## 打包
- 先生成spec文件
- 编辑spec文件
- 根据spec文件生成包
```
nuget spec ./dir
nuget pack ./dir.nuspec
```

## 缓存
查看缓存
```
nuget locals all -list
```
配置缓存环境变量
```
NUGET_HTTP_CACHE_PATH
NUGET_PAKCAGES
```