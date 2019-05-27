
# npm

```bash
npm start   //npm run start
npm stop   //是npm run stop的简写
npm test  //是npm run test的简写
npm restart  //是npm run stop && npm run restart && npm run start的简写 --save:将包的名称及版本号放在dependencies里面
```

# brew

安装

```bash
 /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

常用命令

```bash
brew install mysql
brew services start mysql
```

# composer

Composer是 PHP 世界里用于管理项目依赖的工具。

## install composer locally

Firstly, enter your project folder

```bash
cd my-project-foloder
```

then, copy the following 4 lines of code at a time to youre terminal

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

## install composer globally

make composer globally,You can place the Composer PHAR anywhere you wish. If you put it in a directory that is part of your PATH, you can access it globally.

```bash
mv composer.phar /usr/local/bin/composer
```

## check the version

```bash
composer -V  //测试composer有无安装
```

## 更改镜像

不然laravel装不上

```bash
composer config -g repo.packagist composer https://packagist.phpcomposer.com
```

## 使用homebrew安装composer

```bash
brew update
brew tap josegonzalez/homebrew-php
brew tap homebrew/versions
brew install php55-intl
brew install josegonzalez/php/composer
```

# apm

# yarn

# yum

# apt

Ubuntu's Advanced Packaging Tool (APT)

```bash
sudo apt install nmap
sudo apt remove nmap
sudo apt update
sudo apt upgrade

```

## 参考资料