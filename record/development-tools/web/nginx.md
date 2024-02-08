---
title: Nginx
description: 
published: true
date: 2024-02-08T11:19:56.188Z
tags: 
editor: markdown
dateCreated: 2024-02-08T11:19:56.188Z
---

# 用法
> vim /etc/nginx/sites-available/wiki.cxlljj.top
```
server {
    listen       80;
    listen       443 ssl;
    server_name  wiki.cxlljj.top;

    #access_log  /var/log/nginx/host.access.log  main;

    ssl_certificate     /usr/share/nginx/cert/cloudflare_for_vps.crt;
    ssl_certificate_key /usr/share/nginx/cert/cloudflare_for_vps.key;
    ssl_session_cache   shared:SSL:1m;
    ssl_session_timeout 5m;
    ssl_ciphers         HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers  on;

    location / {
        proxy_intercept_errors on;
        proxy_pass http://127.0.0.1:18000; #假设WebSocket监听端口为5055
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $http_host;
        # 向后端传递访客ip
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
# }
```
> sudo ln -s /etc/nginx/sites-available/wiki.cxlljj.top /etc/nginx/sites-enabled/
