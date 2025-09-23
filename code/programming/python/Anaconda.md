---
title: Anoconda
description: 
published: true
date: 2025-09-23T02:23:36.332Z
tags: python
editor: markdown
dateCreated: 2024-02-29T03:20:42.052Z
---

# 环境
界面用法：
>初学 Python 者自学 Anaconda 的正确姿势是什么？ - 猴子的回答 - 知乎
>https://www.zhihu.com/question/58033789/answer/254673663

可以开启terminal后pip install 软件包

修改默认环境路径：
https://stackoverflow.com/questions/37926940/how-to-specify-new-environment-location-for-conda-create

File->Preferences->Configure Conda（.condarc）
添加
```
envs_dirs:
  - D:\envs
```
等同于
```
conda create --prefix=/users/.../yourEnvName python=x.x
```

# 常用指令
```
conda env list
conda create -n sd-webui python=3.10 -y
conda activate sd-webui
conda remove --name 你的环境名 --all
```