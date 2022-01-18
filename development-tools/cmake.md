---
title: Cmake
description: cmake use record
published: true
date: 2022-01-18T08:06:11.989Z
tags: cmake
editor: markdown
dateCreated: 2022-01-18T01:28:55.825Z
---

# 语法
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
