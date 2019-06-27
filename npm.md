# Node Packages Manager

[TOC]

## INTRUCTION:What is NPM

- NPM stands for **Node.js Package Manager**  .
- NPM is the world's largest software registry.
- Using NPM to publish or install packages to or from the NPM registry. 使用npm可以安装、管理项目中所使用的依赖。还可以分享代码，和他人交流。
- NPM consists of three distinct components:
  - the website: to discover packages
  - the Command Line Interface:  the tool developers interact with npm.
  - the registry:  database of JavaScript softwares.

## Installing Node.js and NPM

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

Download node installer and click 'next' to install node.js and npm.

## Checking the Version

Checking the version of your NPM:

```bash
node --version
npm --version
```

or

```bash
node -v
npm -v
```

## Setting up your npm user account

1. Create an account on the website: http://npmjs.org

2. Testing your new account with npm login:

```bash
npm login
# when prompted, enter your username, password and email address.
whoami # return your npm username if successfully logged in
```

## Intruction of packages and modules

- NPM REGISTRY:  A database of JavaScript packages.

- PACKAGE:

  + A package can be a file that is described by a **package.json** file.
  + A package can be a directory that is described by a **package.json** file.
  + A package must contain a **package.json** file in order to be published to the npm registry.

- MODULE:

  + A module can be a file in the **node_modules** directory.
  + A module can be a directory in the **node_modules** directory.
  + A module must can be loaded by the Node.js require() function. It must be on of the following:
    * A folder with a `package.json` file containing a `"main"` field.
    * A folder with an `index.js` file in it.
    * A JavaScript file.

  + Only modules that have a `package.json` file are called `packages`.

- PACKAGE.JSON

  + lists the packages your project depends on
  + Specifies version of packages that you project can use
  + Packages published to the registry must contain a `package.json` file.
  + `package.json` fields:
    * `name`  must be lowercase and one word, and may contain hyphens and underscores.
    * `version`  must be in the form x.x.x
    * `author`  optional
    * `main` The name of the file that will be loaded when you module is required. The default name is **index.js** .

  ```javascript
  {
    "name": "my-awesome-package",
    "version": "1.0.0"
  }
  ```

  

## CONTRIBUTE: Creating a PACKAGE.JSON file

### npm init

By running `npm init` to create a customized `package.json` file.

```bash
cd /path/to/package
npm init
# Answer the questions in the command line
```

### npm init —yes

By running `npm init —yes` to create a default `package.json` file.

```bash
cd /path/to/package
npm init --yes
```

Example

```json
{
    "name": "my_package",
    "description": "",
    "version": "1.0.0",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "repository": {
      "type": "git",
      "url": "https://github.com/ashleygwilliams/my_package.git"
    },
    "keywords": [],
    "author": "",
    "license": "ISC",
    "bugs": {
      "url": "https://github.com/ashleygwilliams/my_package/issues"
    },
    "homepage": "https://github.com/ashleygwilliams/my_package"
  }
```

## CONTRIBUTE: Creating Node.js modules

Create a package.json

```bash
mkdir first-module-zjsonic
cd first-module-zjsonic
npm init
vi index.js
npm publish # publish your module
```

## GETTING: Searching for and choosing packages

Using npm search bar

## GETTING: Downloading and installing packages

Installing package locally:

```bash
npm install <package-name>
```

Installing package globally:

```bash
npm install -g <package-name>
```

## GETTING: Using npm packages in your project

Once you have installed packages in your `node_modules` directory, you can use it in your code:

```JavaScript
//index.js
var lodash = require('lodash')

var output = lodash.without([1,2,3],1)
console.log(output)
```









