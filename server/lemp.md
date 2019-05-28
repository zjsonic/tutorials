# LEMP

You can host multiple domains and subdomains using a single ip address in linux via `nginx server blocks` or `virtual hosts` in apache.

Here is the general assumption for this setup:

- IP Address: 66.42.77.143
- Domain names: buhaoqi.com www.buhaoqi.com api.buhaoqi.com

## Install and Start Nginx

```bash
sudo apt update
sudo apt install nginx
sudo nginx
```

Check any of your domains in your browser to make sure nginx works correctly. The browser will output the nginx default page.

### Setup the directories for each domain/subdomain

Up untill now, all the domains have set up correctly but there is a huge problem, all pointing to the same page. We need to sperate these domains to point to their own pages. For this, I will setup the directories and html pages.

```bash
cd /var/www/
mkdir buhaoqi.com api.buhaoqi.com
touch buhaoqi.com/index.html api.buhaoqi.com/index.html
```

### Creating server blocks for each domain/subdomain

Nginx provides default server block in /etc/nginx/sites-available/default. We will copy the server block for each domain and do modifications for each.

```bash
cp /etc/nginx/sites-available/default /etc/nginx/sites-available/buhaoqi.com
ln -s /etc/nginx/sites-available/buhaoqi.com /etc/nginx/sites-enabled/buhaoqi.com
```

```bash
server {
   # listen:监听所有的ipV4的地址
   listen 80 default_server;
   # listen: 监听所有的ipv6的地址
   listen [::]:80 default_server;
   # root 站点根目录
   root /var/www/buhaoqi.com;
   # index 站点默认页
   index index.html index.php;
   # server_name 不同域名会通过请求头中的host字段匹配到特定到server块
   server_name buhaoqi.com;
}
```

### Configure Firewall

```bash
sudo ufw allow OpenSSH
sudo ufw allow 80
sudo ufw allow 433
sudo ufw allow ssh
sudo ufw allow 'Nginx HTTP'
sudo ufw enable
sudo ufw status
sudo ufw disable
```

## Install MySQL

```bash
sudo apt install mysql-server
sudo mysql_secure_installation
```

## Install PHP

```bash
sudo apt install php-fpm php-opcache php-cli php-gd php-curl php-mysql
```

## Configure Nginx to Process php File

```bash
server {

    # . . . other code

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.2-fpm.sock;
    }
}

```

## references
- ![https://hackprogramming.com/how-to-setup-subdomain-or-host-multiple-domains-using-nginx-in-linux-server/](https://hackprogramming.com/how-to-setup-subdomain-or-host-multiple-domains-using-nginx-in-linux-server/)

- ![https://linuxize.com/series/how-to-install-lemp-stack-on-ubuntu-18-04/](https://linuxize.com/series/how-to-install-lemp-stack-on-ubuntu-18-04/)