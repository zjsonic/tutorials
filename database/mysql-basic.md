# MySQL Basic

## 登录MySQL
```
$ sudo mysql -u root -p
```

## 查看数据库
```
$ SHOW DATABASES;
```

## 创建数据库
```
$ CREATE DATABASE dbname;
```

## 创建用户
- 赋予所有权限
```
$ GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'e%okla259775';
```
- 赋予特定权限
```
GRANT SELECT ON *.* TO 'username'@'localhost';
```

## 切换数据库
```
$ USE dbname;
```







## 参考
- [https://www.a2hosting.com/kb/developer-corner/mysql/managing-mysql-databases-and-users-from-the-command-line](https://www.a2hosting.com/kb/developer-corner/mysql/managing-mysql-databases-and-users-from-the-command-line)
