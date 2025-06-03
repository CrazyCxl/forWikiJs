---
title: Cmake
description: cmake use record
published: true
date: 2025-06-03T03:31:52.110Z
tags: cmake
editor: markdown
dateCreated: 2024-02-08T11:01:19.009Z
---

# 语法
## 用法
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

## 技巧
设置main项目输出和lib项目一致
```
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/src/")
```