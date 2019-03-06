# Question Logs

## Permission when Install Drupal

>>>
go to the folder where you installed drupal. Ex:
cd /var/www/drupal
then
sudo chown www-data -R sites
Now try installing again.

## drupal 404
分析：首页能打开 其他页打不开
问题：rewrite模块没有开启
解决：
- apache服务器，直接去开启
- nginx服务器，修改default.conf文件
```
location / {
        ## 注释掉下面这行
        #try_files $uri $uri/ =404;
        ## 添加下面这行
        try_files $uri $uri/ /index.php$is_args$args;
    }
```

## 重启nginx命令有何差异？
第一种
```
$ sudo service nginx restart
```
第二种
```
$ sudo systemctl reload nginx
```
第三种
```
$ sudo systemctl restart nginx
```
第四种
```
$ sudo /etc/init.d/nginx reload
```
- 据说restart没有缓存，reload有缓存


## DRUPAL:TRUSTED HOST SETTINGS:Not enabled
>The trusted_host_patterns setting is not configured in settings.php. This can lead to security vulnerabilities. It is highly recommended that you configure this. See Protecting against HTTP HOST Header attacks for more information.

解决：`sites/default/settings.php`下搜索`trusted`， 根据说明做相应修改即可
```
$settings[‘trusted_host_patterns’] = array(
‘^example\.com$’,
‘^www\.example\.com$’
);
```
注意：别犯晕，php的注释是多行注释，简单的去掉`*`号是没用的。


## 1.toString()
- 问题描述：通过`toString()`方法把数字`1`转换成字符串`‘1’`,我眼中的代码是这样写：`1.toString()`，但是会报错：
```
Uncaught SyntaxError: Invalid or unexpected token
```
- 原因：JavaScript解析器眼中的代码是这样：`1.` `toString()`,解析器把数字`1`后面的`.`看做是数字`1`的一部分，所以会报错。
- 解决：`1..toString()` 或 `(1).toString()`


## MongoDB
>Failed to start mongod.service: Unit mongod.service not found.
解决办法：
```
$ sudo systemctl enable mongod
```

## upload_max_filesize(PHP.ini)

```
Loaded Configuration File	/etc/php/7.0/fpm/php.ini

post_max_size = 8M
upload_max_filesize = 2M

sudo nano /var/www/html/info.php
<?php
phpinfo();
?>

sudo service php7.0-fpm restart
```