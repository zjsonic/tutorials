# MySQL Basic

## 常用命令
```
$ sudo mysql -u root -p //登录数据库  default passwords is nothing
$ SHOW DATABASES;  //查看数据库列表
$ CREATE DATABASE dbname; //创建数据库
$ GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY '123456'; //创建用户赋予所有权限
$ GRANT SELECT ON *.* TO 'username'@'localhost'; //创建用户赋予特定权限
$ USE dbname; //切换数据库
```




## 参考
- [https://www.a2hosting.com/kb/developer-corner/mysql/managing-mysql-databases-and-users-from-the-command-line](https://www.a2hosting.com/kb/developer-corner/mysql/managing-mysql-databases-and-users-from-the-command-line)
