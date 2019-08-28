<!-- TITLE: Python -->
<!-- SUBTITLE: A quick summary of Python -->

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