# Sass Basic

## 什么是Sass
- Sass是CSS的元语言.
- 用于描述CSS语言.
- Sass是css的预处理器


## 什么是compass
- 基于sass的CSS开发框架
- Compass可以让你书写css代码变得简单

## 安装Sass
第一步: 安装Ruby(Mac OX自带Ruby)
第二步: 安装Compass(自带安装sass,基于sass)
```
$ sudo gem install compass
```
第三步: 查看版本
```
$ compass -v
```
或
```
$ sass -v
```

## 创建项目
```
compass create my-project
```
项目结构说明:
```
.sass-cache // 快速生成css文件的cache文件
sass // 需要编译的sass文件
stylesheets // 编译后的css文件
config.rb // 项目的默认配置文件
```

## 开启自动编译
在项目根目录下(也就是config.rb所在目录)运行
```
compass watch
```




