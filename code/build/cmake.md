---
title: Cmake
description: cmake use record
published: true
date: 2026-02-06T02:57:55.870Z
tags: cmake
editor: markdown
dateCreated: 2024-02-08T11:01:19.009Z
---

# 语法
## 用法
### ctest运行多个命令
添加```run.cmake```
```
# 顺序执行多个命令
execute_process(
    COMMAND ${MY_EXECUTABLE} arg1 arg2
    RESULT_VARIABLE result1
    OUTPUT_VARIABLE output1
    ERROR_VARIABLE error1
)

if(NOT result1 EQUAL 0)
    message(FATAL_ERROR "Command 1 failed: ${error1}")
endif()

execute_process(
    COMMAND ${ANOTHER_EXECUTABLE} --option value
    RESULT_VARIABLE result2
    OUTPUT_VARIABLE output2
    ERROR_VARIABLE error2
)

if(NOT result2 EQUAL 0)
    message(FATAL_ERROR "Command 2 failed: ${error2}")
endif()

message(STATUS "All commands executed successfully")
```
主cmake里添加ctest
```
# 添加一个自定义目标来运行多个命令
enable_testing()
add_test(
    NAME MyComplexTest
    COMMAND ${CMAKE_COMMAND} 
    	-DTEST_CONFIG=$<CONFIG>
      -DDATA_PATH=${PATH_VAR}
    -P ${CMAKE_CURRENT_SOURCE_DIR}/run_test.cmake
)
```
#### 封装函数
```
function(run_and_check)
    set(options)
    set(oneValueArgs EXEC EXPECT)
    set(multiValueArgs ARGS)
    cmake_parse_arguments(RAC "${options}" "${oneValueArgs}" "${multiValueArgs}" ${ARGN})

    execute_process(
        COMMAND ${RAC_EXEC} ${RAC_ARGS}
        RESULT_VARIABLE result
        OUTPUT_VARIABLE output
        ERROR_VARIABLE error
        OUTPUT_STRIP_TRAILING_WHITESPACE
        ERROR_STRIP_TRAILING_WHITESPACE
    )

    if(NOT result EQUAL 0)
        message(FATAL_ERROR "Command failed:\n${error}")
    endif()

    string(FIND "${output}" "${RAC_EXPECT}" pos)
    if(pos EQUAL -1)
        message(FATAL_ERROR
            "Expected string '${RAC_EXPECT}' not found\n"
            "Output:\n${output}"
        )
    endif()
endfunction()
```
eg.
```
run_and_check(
    EXEC ${MY_EXECUTABLE}
    ARGS arg1 arg2
    EXPECT "EXPECTED_STRING"
)

run_and_check(
    EXEC ${ANOTHER_EXECUTABLE}
    ARGS --option value
    EXPECT "DONE"
)
```
### 同时打包Debug和Release
对于单配置生成器：https://cmake.org/cmake/help/v4.1/guide/tutorial/Packaging%20Debug%20and%20Release.html
创建额外的生成配置```MultiCPackConfig.cmake```
```
include("release/CPackConfig.cmake")

set(CPACK_INSTALL_CMAKE_PROJECTS
    "debug;Tutorial;ALL;/"
    "release;Tutorial;ALL;/"
    )
```
>cpack --config MultiCPackConfig.cmake

对于多配置生成器(vs)
>cpack -C "Debug;Release"

### 设置relwithdebinfo禁用优化
```
SET(CMAKE_CXX_FLAGS_RELWITHDEBINFO "-Od -Ob0 -ZI")
```
### 设置vs分组
参考：https://stackoverflow.com/questions/31422680/how-to-set-visual-studio-filters-for-nested-sub-directory-using-cmake
```
function(assign_source_group)
    foreach(_source IN ITEMS ${ARGN})
        if (IS_ABSOLUTE "${_source}")
            file(RELATIVE_PATH _source_rel "${CMAKE_CURRENT_SOURCE_DIR}" "${_source}")
        else()
            set(_source_rel "${_source}")
        endif()
        get_filename_component(_source_path "${_source_rel}" PATH)
        string(REPLACE "/" "\\" _source_path_msvc "${_source_path}")
        source_group("${_source_path_msvc}" FILES "${_source}")
    endforeach()
endfunction(assign_source_group)
```

### 传递库
注意，cmake要求要么都带PUBLIC等关键字，要么都不带
```
target_link_libraries(my_lib
  PUBLIC 
    debug       Boost::boost_d     # Debug版本Boost（会传递给使用者）
    optimized   Boost::boost       # Release版本Boost（会传递给使用者）
    
  PRIVATE
    debug       InternalLib_d      # 内部Debug库（不传递）
    optimized   InternalLib        # 内部Release库（不传递）
)
```

### 设置RPATH
```
# 不把 rpath 裁掉
set(CMAKE_SKIP_BUILD_RPATH FALSE)
set(CMAKE_SKIP_INSTALL_RPATH FALSE)
set(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)

# 构建 / 安装 rpath
set_target_properties(myapp PROPERTIES
    BUILD_RPATH   "$ORIGIN/../lib"
    INSTALL_RPATH "$ORIGIN/../lib"
)
```
设置测试时的依赖
```
set_property(TEST mytest1 mytest2 PROPERTY
    ENVIRONMENT "LD_LIBRARY_PATH=/path/to/lib"
)
```
## 技巧
设置main项目输出和lib项目一致
```
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/src/")
```