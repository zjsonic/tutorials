# Linux Commands

```bash
sudo apt-get update
chmod o+w filename
sudo ufw enable // 开启防火墙
sudo ufw default deny //随系统启动同时关闭所有外部对本机的访问
sudo ufw disable
sudo ufw status
sudo ufw allow 80 //允许外网访问80端口
sudo ufw allow 'Nginx HTTP'
sudo ufw allow from 192.168.1.1 //允许此IP访问所有的本机端口
sudo ufw deny smtp //禁止外部访问smtp服务
sudo ufw delete allow smtp //删除上面建立的某条规则

```

修改文件或文件夹读写权限

## echo

`echo`: 用于向标准输出设备上输出文本字符串

```bash
echo Hello! World!  // Hello! World!
echo "Hello! World!" // Hello! World!
echo 'Hello! "zhangsan"' // Hello! "zhangsan"
echo "Hello! \"zhangsan\"" // Hello! "zhangsan"
echo -e "You know nothing. \n\t- Ygritte"  // -e: 激活转义字符
echo -e "#Learn Git" > README.md // 重定向输出(到一个文件)，文件不存在则创建一个新文件  > :文件被覆盖
echo -e "# Learn Git" >> README.md //重定向输出(到一个文件) 文件不存在则创建一个新文件 >>: 文件被添加
```

## touch

`touch`：allow us to update the timestamp on existing files and directories as well as creating new, empty files.

```bash
touch file1 //创建或修改一个文件
touch file1 file2 file3  //创建或修改多个文件
touch -C file1 // -C: --no-create  only update the timestamp ,otherwise it will do nothing
```

## 参考

![LinuxIZE.com](http://www.linuxize.com)


server {
        listen 80;
        root /var/www/html/buhaoqi.com;
        index index.php index.html index.htm index.nginx-debian.html;
        server_name buhaoqi.com;

        location / {
                try_files $uri $uri/ =404;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        }

        location ~ /\.ht {
                deny all;
        }
}