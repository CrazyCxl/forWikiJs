---
title: Poco
description: poco used
published: true
date: 2020-10-28T06:32:04.319Z
tags: poco c++
---

# windows字符编码
## json序列化时支持Unicode字符
```
    Poco::JSON::Stringifier::stringify(obj,os,0,-1,JSON_ESCAPE_UNICODE|JSON_WRAP_STRINGS);
```

## 转码
```
    Poco::Latin1Encoding latin1;
    Poco::UTF8Encoding utf8;
    Poco::TextConverter converter(utf8, latin1);
```