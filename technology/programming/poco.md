---
title: Poco
description: poco used
published: true
date: 2020-10-28T07:05:32.445Z
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

```
	Object::Ptr object = result.extract<Object::Ptr>();
	Var test = object->get("test");

	Poco::Latin1Encoding latin1;
	Poco::UTF8Encoding utf8;
	Poco::TextConverter converter(latin1, utf8);
	std::string original;
	converter.convert(text, original);
```
