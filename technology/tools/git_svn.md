---
title: git_svn
description: A quick summary of 版本控制
published: true
date: 2024-10-14T07:28:14.806Z
tags: git, svn
editor: markdown
dateCreated: 2024-02-08T11:03:59.252Z
---

# Git
学习:https://learngitbranching.js.org

## 生成ssh key
```
ssh-keygen -t rsa -b 4096 -C "chenxiaolong0001@foxmail.com"
```

## 使用镜像加速
https://gh-proxy.com/
示例
git clone https://gh-proxy.com/https://github.com/stilleshan/ServerStatus

## 配置
*~/.gitconfig*
### 添加用户和邮箱
>git config user.name "xxx"  
git config user.email 'xxx@xxx.com' 

### Windows配置取消换行告警
```
LF will be replaced by CRLF the next time Git touches it
```
>git config --global core.autocrlf false
### 使用meld作为比较工具
>git config --global  diff.tool  meld

使用
>git difftool HEAD HEAD^1

## 常用命令
### 浅层clone
```
git clone --depth 1 <repository-url>
 ```
 
### 使用 proxy clone
```
export https_proxy=http://127.0.0.1:28081
git clone https://github.com/username/repo.git
```
小技巧代理下载：
```
export https_proxy=http://127.0.0.1:28081
curl -L -O  https://github.com/ultralytics/yolov5/releases/download/v5.0.0/arial.ttl
```

### windows上清空tag
参考：https://stackoverflow.com/questions/1841341/remove-local-git-tags-that-are-no-longer-on-the-remote-repository

>git fetch --prune <remote> "+refs/tags/*:refs/tags/*"


### 修改提交的用户名
> git commit --amend --author="Author Name \<email@address.com\>" --no-edit

### 同步分支

merge时保留冲突的一方
```
# keep remote files
git merge --strategy-option theirs
# keep local files
git merge --strategy-option ours
```
### 子模块
```  
#init
git submodule update --init --recursive  
git submodule update --init third_party/re2
  
#update
git pull --recurse-submodules
```
  
## 远程仓库
**git remote**

- 不带参数：列出已经存在的远程分支
- -v | --verbose： 列出详细信息，在每一个名字后面列出其远程url
- add <名称> <地址>：地址可以为本地或网络路径
- remove <名称>
- rename <当前名称> <新名称>
- set-url <名称> <新地址>


**git fetch**

- <仓库名>：如`git remote add 的名称`


# SVN
## 常用命令

删除未添加到版本库的文件[^svnRemove]
>svn cleanup . --remove-unversioned

[^svnRemove]:https://stackoverflow.com/questions/2803823/how-can-i-delete-all-unversioned-ignored-files-folders-in-my-working-copy