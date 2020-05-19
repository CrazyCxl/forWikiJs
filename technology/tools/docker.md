---
title: Docker
description: normal docker cmds
published: true
date: 2020-05-19T03:39:29.551Z
tags: docker, tool
---

# 显示
```
docker images 
docker ps -a
```

# Image
## 提交container修改到image
提交nginx_base container到一个未命名image
```
docker commit nginx_base

#查询
➜  docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
<none>              <none>              25e9f851ba51        4 seconds ago       20.2MB
nginx               alpine              76defd22aa2c        3 weeks ago         20.2MB

#命名
docker tag 25e9f851ba51 hi_cxl_nginx
```
提交修改到一个已存在的image
```
➜  docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
117494e7e7df        hi_cxl_nginx        "nginx -g 'daemon of…"   3 minutes ago       Up 3 minutes        0.0.0.0:80->80/tcp   hi_cxl
docker commit --message 'this is version 2 of cxl nginx' 117494e7e7df hi_cxl_nginx
```

## 导出
```
docker save hi_cxl_nginx > hi_cxl_nginx.tar
```

# Container
```
#根据image启动一个container
docker run --name hi_cxl -d -p 80:80 hi_cxl_nginx

#根据image创建一个container
docker create --name nginx_base -p 80:80 nginx:alpine
docker start nginx_base
docker cp index.html nginx_base:/user/share/ngix/html/index.html
```

# 总结
启动一个image后会创建一个container