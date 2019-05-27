# Laravel

## System requirements

- PHP >= 7.1.3 (Y)
- OpenSSL PHP Extension : (Y) dependencies for mysql
- PDO PHP Extension
- Mbstring PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension
- Ctype PHP Extension
- JSON PHP Extension
- BCMath PHP Extension

## 常用命令
```
$ composer global require laravel/installer //安装laravel 注意： composer的服务器改为国内镜像
$ laravel   //测试安装成功过
$ laravel new application
$ cd application
$ php artisan serve
``

## 编辑$PATH 路径变量
```
$ laravel  //-bash: laravel: command not found
$ nano ~/.bash_profile  // export PATH="$PATH:$HOME/.composer/vendor/bin"
```
The PATH environment variable tells your system where to look when you run a command. By default ~/.composer/vendor/bin will not be in your PATH. Therefore, if you just attempt to run the command laravel after installing it via composer, your terminal will give you an error saying the command is not found. But if you use the entire path to the command (~/.composer/vendor/bin/laravel), it will execute successfully.

When you run the command composer global require "laravel/installer=~1.1", composer puts the laravel installer into the directory ~/.composer/vendor/bin (in *nix, ~ represents your home directory). Adding ~/.composer/vendor/bin to your PATH allows you to just execute the command laravel instead of having to use the full path of ~/.composer/vendor/bin/laravel.
