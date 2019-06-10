# Linux

## 文件夹含义

- ubuntu
  - `/bin/`:用以存储二进制可执行命令文件
  - `/etc/` :存放文件管理配置文件和目录
  - `/var/`    用于存放很多不断变化的文件，例如日志文件等
  - `/lib/`    存储各种程序所需要的共享库文件。

## Wget: Download File via HTTP/FTP

wget: A free utility for downloading files from the web. It supports `HTTP` `HTTPS` `FTP` protocols.

Installing wget

```bash
sudo apt-get install wget
```

## curl: Transfer Data to or from  a server

`curl`:The curl command transfers data to or from a network server on Mac OS, using one of the supported protocols (HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, DICT, TELNET, LDAP or FILE). It is designed to work without user interaction, so it is ideal for use in a shell script.

```bash
curl [options] [URL...]
curl 'url'
curl [option] 'url'
curl -O 'url' # Capital O write output to a file named like the remote we get
curl -L -O 'url'
curl -o output.file.name.here 'url-here'
curl -o foo.pdf 'http://server1.cyberciti.biz/foo.pdf'

```

```bash
wget http://website.com/files/file.zip
```




## sudo install

```bash
sudo ....   //以系统管理员(root)身份执行指令
sudo -V //查看sudo命令对版本号
sudo install xxx  //如果需要，则手动选择Yes安装
sudo install -y xxx //自动选择Yes按照

```

## sudo apt update

```bash
sudo apt-get update
chmod o+w filename
```

## sudo ufw

```bash
sudo ufw status # check the ubuntu firewall's status
sudo ufw disable # disable the ubuntu firewall
sudo ufw allow ssh # add a rule
sudo ufw allow 80 # add a rule
sudo ufw allow 'Nginx HTTP' # add a rule
sudo ufw allow from 192.168.1.1 //允许此IP访问所有的本机端口
sudo ufw deny smtp //禁止外部访问smtp服务
sudo ufw delete allow smtp //删除上面建立的某条规则
sudo ufw enable // 开启防火墙
sudo ufw default deny //随系统启动同时关闭所有外部对本机的访问
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