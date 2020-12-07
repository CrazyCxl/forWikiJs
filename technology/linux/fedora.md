---
title: Fedora
description: A quick summary of Fedora
published: true
date: 2020-12-07T08:35:25.874Z
tags: 
---

配置相关
===
防火墙
---
### Firewall
>firewall-cmd --add-service=http --permanent
firewall-cmd --permanent [--zone=public] --add-port=21/tcp
firewall-cmd --reload
firewall-cmd --zone=public --remove-port=8085/tcp
firewall-cmd --runtime-to-permanent
firewall-cmd --reload
firewall-cmd --list-all
firewall-cmd --list-all-zones

#### 新ssh端口
https://serverfault.com/questions/746548/firewalld-if-i-change-the-ssh-service-port-is-it-enough-to-allow-the-new-port
copy ```/usr/lib/firewalld/services/ssh.xml``` to ```/etc/firewalld/services/ssh.xml```
and modify it for your purpose.
You then need to relod the configuration
```
firewall-cmd --reload
```
### SELinux
列出端口标签：
> semanage port -l

添加端口标签：
> emanage port -a -t PORT_TYPE -p tcp 8085

PORT_TYPE: 

 - http_cache_port_t
 - http_port_t
 - jboss_management_port_t
 - jboss_messaging_port_t
 - ntop_port_t
 - puppet_port_t

示例
> semanage port -a -t http_port_t -p tcp 82

删除端口标签示例
> semanage port -d -t http_port_t -p tcp 82

定时任务
---
### 命令`crontab`
![crontab格式说明](http://img.blog.csdn.net/20160804170302727)
参数：

 - -l 列出已添加的任务
 - -e 编辑任务
 - -u 指定用户

示例：

每天 02:00 执行任务
```
0 2 * * * /bin/sh backup.sh
```

每天 5:00和17:00执行任务
```
0 5,17 * * * /scripts/script.sh
```

每分钟执行一次任务
```
* * * * *  /scripts/script.sh
```

每 10min 执行一次任务
```
*/10 * * * *  /scripts/script.sh
```

常用命令
===
使用locate查询库位置
---
### 示例：
>locate xxx.so

输出

>/usr/lib/xxx.so.1
/usr/lib/xxx.so.1.2.0
/usr/lib64/xxx.so



包管理
===
列出repos
```
yum repolist all
yum repolist
yum repolist enabled
yum repolist disabled
```
管理repos
```
yum-config-manager --enable repository
yum-config-manager --disable repository
```
查询包含的rpm包
```
sudo yum whatprovides "libmysqlclient*"
```

问题&解决
===
**Q:** 虚拟机共享粘贴版不可用？

**A:** 查看spice-vdagent是否安装