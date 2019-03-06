# Mongodb Basic

## 学Mongodb
- 教程:[https://www.tutorialspoint.com/mongodb/mongodb_create_collection.htm](https://www.tutorialspoint.com/mongodb/mongodb_create_collection.htm)

## Profile
- mongodb is a document database.
- document database: data structure composed of key/value pairs. similar to JSON objects.

## Installation
- 安装参考：[how-to-install-and-secure-mongodb-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-mongodb-on-ubuntu-16-04)
- mongodb数据库存放位置（默认）：`var/lib/mongodb`
- mongodb日志的存放位置：`var/log/mongodb/mongod.log`
- mongodb可执行文件位置：`/usr/bin/mongo` 和 `/usr/bin/mongod`
- mongodb配置文件的存放位置：`/etc/mongod.conf`

## ubuntu文件夹含义
- `/bin/`:用以存储二进制可执行命令文件
- `/etc/` :存放文件管理配置文件和目录
- `/var/`    用于存放很多不断变化的文件，例如日志文件等
- `/lib/`    存储各种程序所需要的共享库文件。

## 数据库与用户管理
- 参考：[https://blog.csdn.net/u010649766/article/details/78497928](https://blog.csdn.net/u010649766/article/details/78497928)

## Mongodb三大基本概念
- `Database`: `collection`的物理容器。
- `Collection`: 一组相关的`document`
- `Document`: 一组`key/value`对的集合

## 视频网站数据库设计规划
- 每一个video有唯一`title` `description` `url`
- 每一个video有一个或多个`tag`
- 每一个video有`author`和`likes`
- 每一个video有用户发表的`comments`
```
{
    _id: VIDEO_ID,

}
```

## sudo apt-get install mongodb-org

## sudo systemctl start mongod

## sudo service mongod start

## sudo systemctl status mongod

## sudo systemctl stop mongod

## sudo systemctl enable mongod


## create database
return the existing database or create a new database
```
> use DATABASE_NAME
```

## 查看当前使用的数据库
```
> db
```
## show dbs = show databases
```
> show dbs
```
确认访问权限
```
$ mongo -u xxx -p --authenticationDatabase admin
```

## db.dropDatabase()
- `db.dropDatabase()` will delete the selected database.
- if you have not selected any database, then it will delete the `test` database.


## db.createCollection(name,options)
- name: the name of the collection to be created.
- options: optional, a document used to specify configuration of memory size and indexing 

```
use test
db.createCollection('user_vip')
```
```
use test
db.createCollection('user_general',{
    capped: true, // 是否激活capped collections  默认false
    autoIndexId:true, //是否激活在`_id`字段上自动创建索引  默认false
    size:6142800, //为capped collections指定最大字节
    max:10000 // 指定允许创建的document的最大数字
})
```
## show collections
```
> show collections
```

## mongod --path

## mongod --port 27107


## mongo SHELL

## db:变量 指代当前数据库
```
> db
admin
```



## db.COLLECTION_NAME.insert(document)

## authorization:"enabled"
mongodb要求所有的客户端进行身份验证，以确定它们的访问权限。
authentication: 认证。验证用户身份的过程。
authorization: 授权。决定用户可访问的资源和可进行的操作

## 认证方法
认证一个用户，需要提供：
- username
- password
- authentication database

使用mongo shell认证的方式
- 在mongo shell连接数据库实例的时候进行认证
- 先连接数据库实例 然后运行认证命令或认证方法进行认证
    - db.auth()
    - mongo - u xxx -p --authenticationDatabase admin

## db.createUser()
- 必须增加一个数据库对应的用户做认证
- 当增加用户的时候，你可以给用户分配角色

## 认证数据库
当创建用户的时候，必须指定数据库。这个数据库就是用户的认证数据库
- 用户可以拥有跨不同数据库的权限，用户的特权不会限制在认证数据库


## 认证用户



## mongo SHELL
`mongo Shell`是一个与`mongodb`数据库交互的js接口。
- 可进行CRUD操作
- 可进行管理操作
mongo shell是mongodb的组件。一旦安装了mongodb就可以使用mongo shell连接到数据库实例

## mongo --port 27017
连接本地默认端口的数据库实例,默认端口可省略
```
mongo  
```
连接本地非默认端口的数据库实例

```
mongo --port 28015
```
连接远程数据库实例
```
mongo -u AdminSammy -p --authenticationDatabase admin --host IP_address_of_MongoHost
```
或
```
mongo --host mongodb0.example.com --port 28015
```
或
```
mongo --host mongodb0.example.com:28015
```

或
```
mongo mongodb://mongodb0.example.com:28015
```

## db
显示当前使用的数据库
```
> db   // 默认为test
```
## use DATABASE_NAME
切换数据库
```
> use DATABASE_NAME  //可以切换到non-existing数据库
```
## show dbs
列出可用数据库
```
> show dbs
```
## exit the shell
```
> quit()
```
或 `ctl+C`