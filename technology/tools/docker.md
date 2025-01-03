---
title: Docker
description: normal docker cmds
published: true
date: 2025-01-03T06:07:03.501Z
tags: docker, tool
editor: markdown
dateCreated: 2024-02-08T11:03:45.948Z
---

# 加速
## 修改为国内源
阿里云加速地址获取：
https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors

修改或添加`/etc/docker/daemon.json `
```
{
"registry-mirrors": [
“https://q151ft4n.mirror.aliyuncs.com”，
"https://registry.docker-cn.com",
"http://hub-mirror.c.163.com"
],
"dns": ["8.8.8.8","8.8.4.4"]
}
```
重启
```
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## 使用代理
参考：https://www.lfhacks.com/tech/pull-docker-images-behind-proxy/
```
sudo mkdir -p /etc/systemd/system/docker.service.d
sudo vim /etc/systemd/system/docker.service.d/http-proxy.conf
```
输入以下内容，注意代理不要绑定到127.0.0.1，可以绑定到0.0.0.0上
```
[Service]
Environment="HTTP_PROXY=http://proxy.example.com"
Environment="HTTPS_PROXY=http://proxy.example.com"
```
然后重启服务
```
sudo systemctl daemon-reload
sudo systemctl restart docker
sudo systemctl show --property=Environment docker
```

# 常用命令
查看
```
docker images 
docker ps -a
#查看映射关系等详情
docker inspect id
```
进入容器
```
docker exec -it 69d1 bash
exit
```
# Image
## 删除
```
docker rmi name
```

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

## 导入导出
```
docker save -o image_name.tar image_name:tag
docker load -i image_name.tar
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
## 导入导出
```
docker export hi_cxl > hi_cxl_container.tar
#导入为新的image
docker import hi_cxl_container.tar hi_cxl_image
```
# 总结
启动一个image后会创建一个container