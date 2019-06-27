# Basic

[TOC]

## What is Node.js

Node.js是基于Chrome的V8引擎构建的JS运行环境。常用来创建web服务器。Node.js可以做一下事情：

- 操作内容：生成动态内容
- 操作文件：可以操作服务器上的文件
- 操作表单：可以操作表单数据
- 操作数据库：可以操作数据库的数据

## Install Node.js

- 方法一：从官网[https://nodejs.org/en/download/](https://nodejs.org/en/download/)直接下载
- 方法二：通过各种package manager安装

Checking the version of Node.js

```bash
node -v
```

or

```bash
node --version
```



## What is NPM

- NPM stands for **Node.js Package Manager**  .
- NPM is the world's largest software registry.
- Using NPM to publish or install packages to or from the NPM registry. 使用npm可以安装、管理项目中所使用的依赖。还可以分享代码，和他人交流。
- NPM consists of three distinct components:
  + the website: to discover packages
  + the Command Line Interface:  the tool developers interact with npm.
  + the registry:  database of JavaScript softwares.

## Install Node.js and NPM

### Using the Node version manager (recommended)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

Verify Installation:

```bash
command -v nvm
```

which should output 'nvm' if the installation was successful.

### Using a Node installer

Checking the version of your NPM:

```bash
npm --version
```

or

```bash
npm -v
```

## Usages

Install the latest release of node:

```bash
nvm install node # node is an alias for the lastest version.
```

To install a specified version:

```bash
nvm install 6.14.4 # or 10.10.0, 8.9.1, etc
```

To list the available version:

```bash
nvm ls-remote
```

Use the installed version:

```bash
nvm use node
```

## Starting Node.js

启动Node.js就是启动Node.js的解释器。有两种方式：

方式一：启动Node交互模式

```node.js
node
```

方式二：启动Node运行模式

```node.js
node hello.js
```

