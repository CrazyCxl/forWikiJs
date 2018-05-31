<!-- TITLE: Windows -->
<!-- SUBTITLE: Windows 下的编程问题 -->


# 库相关
## DLL库信息与依赖查看

dependencywalker 工具：http://www.dependencywalker.com/

## Qt使用QLibary加载dll库失败[^dll_error]

使用 `SetDllDirectory`[^dll_lib] 后再加载

[^dll_error]:https://stackoverflow.com/questions/22354639/loading-library-with-dependency-with-qlibrary
[^dll_lib]:https://msdn.microsoft.com/en-us/library/ms686203%28VS.85%29.aspx
