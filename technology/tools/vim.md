---
title: Vim
description: A quick summary of Vim
published: true
date: 2022-11-24T07:12:57.874Z
tags: 
editor: markdown
dateCreated: 2020-03-19T08:38:40.460Z
---

# 常用命令
## 显示行号
```
:set number
```

sudo 保存
---
```
: w !sudo tee %
```
替换
---
```：[addr]s/源字符串/目的字符串/[option]```

 ```[addr]``` 表示检索范围，省略时表示当前行。

 - “1，20” ：表示从第1行到20行
 - “%” ：表示整个文件，同“1,\$”
 -  “. ,\$” ：从当前行到文件尾

```s``` : 表示替换操作
```[option]``` : 表示操作类型

- g 表示全局替换; 
- c 表示进行确认
- p 表示替代结果逐行显示（Ctrl + L恢复屏幕）；
- 省略option时仅对每行第一个匹配串进行替换；
- 如果在源字符串和目的字符串中出现特殊字符，需要用”\”转义

# 配置
在基础配置上添加行号```vim ~/.vimrc```
```
unlet! skip_defaults_vim
source $VIMRUNTIME/defaults.vim
set number
```