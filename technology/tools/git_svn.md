---
title: git_svn
description: A quick summary of 版本控制
published: true
date: 2023-04-25T06:36:59.325Z
tags: git, svn
editor: markdown
dateCreated: 2020-03-19T08:38:43.421Z
---

# Git
学习:https://learngitbranching.js.org
## 配置
*~/.gitconfig*
### 添加用户和邮箱
>git config user.name "xxx"  
git config user.email 'xxx@xxx.com'  
### 使用meld作为比较工具
>git config --global  diff.tool  meld

使用
>git difftool HEAD HEAD^1

## 常用命令
### 使用 proxy clone
```
export https_proxy=http://127.0.0.1:28081
git clone https://github.com/username/repo.git
```

### windows上清空tag
参考：https://stackoverflow.com/questions/1841341/remove-local-git-tags-that-are-no-longer-on-the-remote-repository

>git fetch --prune <remote> "+refs/tags/*:refs/tags/*"


### 修改提交的用户名
> git commit --amend --author="Author Name <email@address.com>" --no-edit

### 同步分支
参考：https://www.jianshu.com/p/c17472d704a0
merge --ff-only 与 rebase 功能类似

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