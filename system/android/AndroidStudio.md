---
title: Andriod Studio
description: Andriod Studio Ide
published: true
date: 2023-12-21T03:42:36.038Z
tags: ide
editor: markdown
dateCreated: 2023-06-26T07:47:36.653Z
---

# install
## sdk 下载失败
>host里修改从 http://ping.chinaz.com/ 获取的 ```dl.google.com``` ip
或者修改proxy为 ```mirrors.neusoft.edu.cn:80```

## gradle下载失败
参考：https://jasonkayzk.github.io/2021/01/13/%E8%A7%A3%E5%86%B3Android%E9%A1%B9%E7%9B%AE%E4%B8%8B%E8%BD%BDGradle%E9%80%9F%E5%BA%A6%E6%9E%81%E6%85%A2%E7%9A%84%E9%97%AE%E9%A2%98/

在项目的gradle/wrapper/gradle-wrapper.properties这个文件中可以看到下载地址
可以将其修改为国内的一个源，如：
```
distributionUrl=https\://code.aliyun.com/kar/gradle-all-zip/raw/master/gradle-6.5-all.zip
```
或者手动下载放到 $User/.gradle/wrapper/dists中创建一个对应版本的文件夹以及下面的一个SHA256签名的目录，直接将zip拷贝进去（无需解压缩）