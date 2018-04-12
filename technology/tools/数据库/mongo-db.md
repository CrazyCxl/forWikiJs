<!-- TITLE: Mongo Db -->
<!-- SUBTITLE: A quick summary of Mongo Db -->

# 下载与安装
## Linux
64位 linux Mongodb 3.0.1 [下载](https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.0.1.tgz)

下载完成后设置环境变量到/etc/profile
>export PATH=$PATH:/path/mongodb-linux-i686-3.0.1/bin

### Fedora
>yum install mongodb-server mongodb mongo-tools

常用命令
===
查询
---
### 查询数据库与表信息
*use 会尝试创建数据库*
>$mongo
\> show dbs
...数据库列表
\> use dbName
switched to db dbName
\> show collections
...表列表
\> exit

### find查询内容
db.collection.find(query, projection)

db.col.find().pretty()
pretty()表示以格式化的方式来显示所有文档。

| 操作 | 格式 | 范例 | RDBMS中的类似语句|
| --------   |
| 等于 | {< key >:< value >} |db.col.find({"by":"菜鸟教程"}).pretty()|where by = '菜鸟教程'|
| 小于 | {< key >:{\$lt:< value >}} | db.col.find({"likes":{\$lt:50}}).pretty()|where likes < 50|
|小于或等于|{< key >:{\$lte:< value >}}|db.col.find({"likes":{\$lte:50}}).pretty()|where likes <= 50|
|大于|{< key >:{\$gt:< value >}}|db.col.find({"likes":{\$gt:50}}).pretty()|where likes > 50|
|大于或等于|{< key >:{\$gte:< value >}} |db.col.find({"likes":{\$gte:50}}).pretty()|where likes >= 50|
|不等于|{< key >:{\$ne:< value >}} |db.col.find({"likes":{\$ne:50}}).pretty()|where likes != 50|

# 备份与恢复
## 备份
mongodump -h dbhost -d dbname -o dbdirectory

- -h：MongDB所在服务器地址，例如：127.0.0.1，当然也可以指定端口号：127.0.0.1:27017
- -d：需要备份的数据库实例，例如：test
- -o：备份的数据存放位置，例如：*c:\data\dump*，当然该目录需要提前建立，在备份完成后，系统自动在dump目录下建立一个test目录，这个目录里面存放该数据库实例的备份数据。
## 恢复
mongorestore -h dbhost -d dbname --directoryperdb/--dir dbdirectory

- -h：MongoDB所在服务器地址
- -d：需要恢复的数据库实例，例如：test，当然这个名称也可以和备份时候的不一样，比如test2
- --directoryperdb：备份数据所在位置，例如：*c:\data\dump\test*，这里为什么要多加一个test，而不是备份时候的dump，读者自己查看提示吧！
- --drop：恢复的时候，先删除当前数据，然后恢复备份的数据。就是说，恢复后，备份后添加修改的数据都会被删除，慎用哦！

### 示例
>mongorestore -h localhost -d leanote --dir /home/user1/leanote_install_data

