# Ngin Default Configuration

## 第一步：解析域名
- 解析example.com
  - 添加a记录
  - host: @
  - 值: 128.168.90.142

注：本例采用example.com演示，如果是是二级域名，直接使用二级域名api.example.com代替example.com
- 解析api.example.com
  - 添加a记录
  - host: api
  - 值: 128.168.90.142

## 第二步: 验证域名所有权
验证域名所有权的方式有很多，这里采用`dns验证方式` + `域名解析商提供的 api 自动添加 txt 记录` , 完成验证。

1. 获取`API Key` 和 `Secret`:
- 登录[https://developer.godaddy.com/keys/](https://developer.godaddy.com/keys/),获取`API Key` 和 `Secret`
- 在选项中，选择创建production环境的key

2. 导出key
```
export GD_Key="sdfsdfsdfljlbjkljlkjsdfoiwje"
export GD_Secret="asdfsdafdsfdsfdsfdsfdsafd"
```

## 第三步：创建证书

```
acme.sh --issue --dns dns_gd -d example.com -d www.example.com
```

## 第四步：拷贝证书

```
acme.sh  --installcert  -d  example.com   \
--key-file   /etc/nginx/ssl/example.com/example.com.key \
--fullchain-file /etc/nginx/ssl/example.com/fullchain.cer \
--reloadcmd  "service nginx force-reload"

```
注意：
- 提前创建好存放证书的路径，不然报错。
- 这里的二级域名采用单独创建的形式，可以泛解析：\*.example.com


## 第五步：绑定主域名+二级域名
配置文件除了绑定主域名和二级域名，同时：
- 配置SSL
- 配置No-www

```
# configuration for https://example.com
server {
          listen 80;
          listen [::]:80;
          server_name example.com www.example.com;
          return 301 https://example.com$request_uri;
  }

  server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name www.example.com;
    return 301 https://example.com$request_uri;

    ssl_certificate /etc/nginx/ssl/fullchain.cer;
    ssl_certificate_key /etc/nginx/ssl/example.com.key;
  }


  server {
          listen 443 ssl http2 default_server;
          listen [::]:443 ssl http2 default_server;
          server_name example.com;
          # return 301 https://example.com$request_uri;

          ssl_certificate /etc/nginx/ssl/fullchain.cer;
          ssl_certificate_key /etc/nginx/ssl/example.com.key;

          root /var/www/example.com/client/dist;
          index index.html index.php index.htm;

          location / {
           try_files $uri $uri/ =404;
          }

          location ~ /.well-known {
           allow all;
          }
  }

  # configuration for https://api.example.com
  server {
         listen 80;
         listen [::]:80;

         listen 443 ssl http2;
         listen [::]:443 http2;

         ssl_certificate /etc/nginx/ssl/api.example.com/fullchain.cer;
         ssl_certificate_key /etc/nginx/ssl/api.example.com/api.example.com.key;

         root /var/www/example.com/server;
         index index.html index.php;

         server_name api.example.com;


         location / {
                 try_files $uri $uri/ =404;
         }

         # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
         #
         location ~ \.php$ {
                include snippets/fastcgi-php.conf;

                # With php7.0-cgi alone:
                # fastcgi_pass 127.0.0.1:9000;
                # With php7.0-fpm:
                fastcgi_pass unix:/run/php/php7.0-fpm.sock;
         }
  }
  ```

## 参考
- [https://github.com/Neilpang/acme.sh](https://github.com/Neilpang/acme.sh)
