<!-- TITLE: My Sql -->
<!-- SUBTITLE: A quick summary of My Sql -->

# 查询

>show databases;
>show tables;

# 导入导出

## 本地
导出数据库
>$ mysqldump -u root -p RUNOOB > database_dump.txt
password \******

导入数据库
>$ mysql -u root -p database_name < dump.txt
password \*****

## 远程
导入数据库
>使用以下命令将导出的数据直接导入到远程的服务器上，但请确保两台服务器是相通的，是可以相互访问的
$ mysqldump -u root -p database_name \
       | mysql -h other-host.com database_name
       
导出数据库
>$ mysqldump -h other-host.com -P port -u root -p database_name > dump.txt
password \****