
## npm
```
npm start   //npm run start
npm stop   //是npm run stop的简写
npm test  //是npm run test的简写
npm restart  //是npm run stop && npm run restart && npm run start的简写

--save:将包的名称及版本号放在dependencies里面


```
## brew
简介
- 使用 Homebrew 安装 Apple 没有预装但 你需要的东西。
- Homebrew 不会将文件安装到它本身目录之外，所以您可将 Homebrew 安装到任意位置。
- 完全基于 Git 和 ruby，所以自由修改的同时你仍可以轻松撤销你的变更或与上游更新合并。
- Homebrew 的配方都是简单的 Ruby 脚本：
- 使用 gem 来安装 gems、用 brew 来安装那些依赖包。
安装
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
升级
```
fds
```

## composer
**Composer是 PHP 世界里用于管理项目依赖的工具.**
对于现代语言而言，包管理器基本上是标配。Java 有 Maven，Python 有 pip，Ruby 有 gem，Nodejs 有 npm。PHP 的则是 PEAR，不过 PEAR 坑不少：

- 依赖处理容易出问题
- 配置非常复杂
- 难用的命令行接口
好在我们有 Composer，PHP依赖管理的利器。它是开源的，使用起来也很简单，提交自己的包也很容易。

安装
```
brew update
brew tap josegonzalez/homebrew-php
brew tap homebrew/versions
brew install php55-intl
brew install josegonzalez/php/composer
```

## apm

## yarn

## yum

## apt


## 参考资料
> - []()
> - []()
