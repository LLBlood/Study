# Centos 8 安装MongoDB

## 一、下载安装包

[mongoDB下载网址

![image-20240123135141836](mongoImages\download.png)

## 二、解压文件

```bash
tar -zxvf mongodb-linux-x86_64-rhel80-4.2.25.tgz
#  重命名
mv mongodb-linux-x86_64-rhel80-4.2.25 mongodbServer
```

## 三、创建配置文件

```bash
# 创建数据库文件夹
mkdir data
# 创建日志文件夹
mkdir log
# 创建配置文件夹与配置文件
mkdir etc
# 配置文件mongodb.conf
cd /disk2/mongo/mongodbServer/etc
vim mongodb.conf
```

```bash
#指定数据库路径
dbpath=/disk2/mongo/mongodbServer/data
#指定MongoDB日志文件
logpath=/disk2/mongo/mongodbServer/log/mongodb.log
#使用追加的方式写日志
logappend=true
#端口号
port=33333
#方便外网访问,外网所有ip都可以访问,不要写成固定的Linux的ip
bind_ip=0.0.0.0
fork=true#以守护进程的方式运行MongoDB,创建服务器进程
#auth=true#启用用户验证
#bind ip=0.0.0.0.0 #绑定服务IP, 着绑定127.0.0.1,则只能本机访问,不指定则默认为地所有IP
```

启动文件

```bash
#!/bin/sh

/disk2/mongo/mongodbServer/bin/mongod --config /disk2/mongo/mongodbServer/etc/mongodb.conf
```

停止文件

```bash
#!/bin/sh

/disk2/mongo/mongodbServer/bin/mongod --shutdown --config /disk2/mongo/mongodbServer/etc/mongodb.conf
```

## 四、创建超级用户

```
./mongo 127.0.0.1:33333
进入mongo
use admin
db.createUser( {user: "pfnieadmin",pwd: "123456",roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]});
show users或db.system.users.find()查看已有用户.
# 这让这名用户能够访问系统中的所有数据库、创建新的数据库以及管理 MongoDB 集群和副本集。
db.createUser( {user: "pfnieadmin",pwd: "123456",roles: [ "readWriteAnyDatabase", "dbAdminAnyDatabase","clusterAdmin"]});
```

## 五、备份文件

```bash
./mongodump --uri="" --collection=order_modify_info --out=/disk2/mongo/mongodbServer/dumpback --gzip -v

# --forceTableScan 强制备份
```

```bash
还原命令 ./mongorestore --host 127.0.0.1:33333  --username pfnieadmin --password 123456 --gzip /disk2/mongo/mongodbServer/dumpback -v
```

