---
title: Python
description: A quick summary of Python
published: true
date: 2023-02-08T07:46:05.250Z
tags: 
editor: markdown
dateCreated: 2020-03-19T08:38:28.707Z
---

# 环境相关
## 国内源
> http://pypi.douban.com/simple/  豆瓣
http://mirrors.aliyun.com/pypi/simple/ 阿里
http://pypi.hustunique.com/simple/ 华中理工大学
http://pypi.sdutlinux.org/simple/ 山东理工大学
http://pypi.mirrors.ustc.edu.cn/simple/  中国科学技术大学
https://pypi.tuna.tsinghua.edu.cn/simple 清华
https://mirror.baidu.com/pypi/simple 百度（推荐）

简单使用：
```
sudo pip install -i http://pypi.douban.com/simple/ flask
```

# C++封装
## boost.python
### Build
Build in windows

```
 ./bootstrap --with-python=python3.7
./b2 stage --toolset=msvc-14.0 --build-type=complete --with-python address-mo
del=32 link=static runtime-link=shared threading=multi debug release
```

### Use
add **boost_1_71_0** and **Python\include** path to INCLUDE_PATH

pro eg.
```
DEFINES += BOOST_PYTHON_STATIC_LIB

INCLUDEPATH += "D:\data\zips\boost_1_71_0\boost_1_71_0" \
               "C:\Users\chenx\AppData\Local\Programs\Python\Python37-32\include"
							 
LIBS += -LC:\Users\chenx\AppData\Local\Programs\Python\Python37-32\libs -lpython37
LIBS += -L$$quote(D:\data\zips\boost_1_71_0\boost_1_71_0\stage\lib)
```

cpp eg.
```
#include <boost/python/module.hpp>
#include <boost/python/def.hpp>
#include <boost/python/class.hpp>
#include "xxx.h"

using namespace boost::python;

BOOST_PYTHON_MODULE(xxx)  // foo will be the name you import in python
{
    class_<xxx>("xxx")  // constructor args
            .def("aaa", &xxx::aaa)  // member function
    ;
}
```
							 
参考：https://www.cnblogs.com/hdtianfu/archive/2012/07/27/2611382.html