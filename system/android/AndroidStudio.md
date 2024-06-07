---
title: Andriod Studio
description: Andriod Studio Ide
published: true
date: 2024-06-07T01:50:29.364Z
tags: ide
editor: markdown
dateCreated: 2024-02-08T11:02:50.492Z
---

# AVD
主机IP:10.0.2.2

# build
## 常见报错
### sdk 下载失败
>host里修改从 http://ping.chinaz.com/ 获取的 ```dl.google.com``` ip
或者修改proxy为 ```mirrors.neusoft.edu.cn:80```

### gradle下载失败
参考：https://jasonkayzk.github.io/2021/01/13/%E8%A7%A3%E5%86%B3Android%E9%A1%B9%E7%9B%AE%E4%B8%8B%E8%BD%BDGradle%E9%80%9F%E5%BA%A6%E6%9E%81%E6%85%A2%E7%9A%84%E9%97%AE%E9%A2%98/

在项目的gradle/wrapper/gradle-wrapper.properties这个文件中可以看到下载地址
可以将其修改为国内的一个源，如：
```
distributionUrl=https\://mirrors.cloud.tencent.com/gradle/gradle-6.5-all.zip
```
或者手动下载放到 $User/.gradle/wrapper/dists中创建一个对应版本的文件夹以及下面的一个SHA256签名的目录，直接将zip拷贝进去（无需解压缩）

### Gradle版本低
报错
>The project uses Gradle 4.1 which is incompatible with Java 11 or newer.

参考：https://blog.csdn.net/m0_65511195/article/details/122148195
File->Settings->Build,Execution,Deployment->Gradle 
里的Gradle JDK改为1.8

### 没找到签名文件keystore.properties
需要自己新建一个，然后根据之后的引用填写内容
```
        release {
            storeFile file(keystoreProperties['RELEASE_STORE_FILE'])
            storePassword keystoreProperties['RELEASE_KEYSTORE_PASSWORD']
            keyAlias keystoreProperties['RELEASE_KEY_ALIAS']
            keyPassword keystoreProperties['RELEASE_KEY_PASSWORD']
        }
```
对应内容
```
RELEASE_STORE_FILE=~/.gradle/release-key.keystore
RELEASE_KEYSTORE_PASSWORD=123456
RELEASE_KEY_ALIAS=key
RELEASE_KEY_PASSWORD=123456
```