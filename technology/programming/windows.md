<!-- TITLE: Windows -->
<!-- SUBTITLE: Windows 下的编程问题 -->

# NSIS打包工具
官网：http://nsis.sourceforge.net/Main_Page

# 库相关
## DLL库信息与依赖查看

dependencywalker 工具：http://www.dependencywalker.com/

## Qt使用QLibary加载dll库失败[^dll_error]

使用 `SetDllDirectory`[^dll_lib] 后再加载

## Q&A

vs运行qt程序时相对路径访问失败
>vs 默认当前目录为工程目录，而不是可自行程序所在的目录

[^dll_error]:https://stackoverflow.com/questions/22354639/loading-library-with-dependency-with-qlibrary
[^dll_lib]:https://msdn.microsoft.com/en-us/library/ms686203%28VS.85%29.aspx
