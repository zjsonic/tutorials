# Vue Cli 3 Start


## Vue CLI
Vue CLi是一个全局安装的npm包，并且提供了vue命令。


- cli服务建立在webpack配置之上
- 基于插件的构架 可以加载其他插件(插件你向项目提供具有某种功能的的npm包，可复用的preset)
- 提供vue-cli-service命令

## vue serve(快速原型开发)
- 在文件目录下，执行vue serve ,对单个vue文件进行快速原型开发（先安装全局扩展：npm install -g @vue/cli-service-global）
- `vue serve`使用项目的默认配置
  - 它会在当前目录自动推导入口文件：main.js index.js App.vue app.vue
  - 可以显示指定入口文件：vue serve aaa.vue

## vue build(快速原型开发)
将目标文件构建成一个生产环境的包并用来部署
```
vue build MyComponent.vue
```



## vue create
创建一个新项目
## vue ui
使用图形化界面创建和管理项目



## 插件
- 查看package.json文件，很多插件都是以`@vue/cli-plugin-`开头
- 插件可以修改webpack配置
- 也可以向vue-cli-service注入新命令

## vue add

在现有项目中添加插件
```
vue add @vue/eslint
```
## vue-cli-service
自动解析package.json文件。也就是说加载package.json文件中列出的所有cli插件.

## vue-cli-service build
在dist/ 目录产生一个可用于生产环境的包

## vue-cli-service inspect
审查一个 Vue CLI 项目的 webpack config

## npx vue-cli-service help
查看所有注入命令

## public/index.html
- 项目首页的模板文件
- 该文件会被`html-webpack-plugin`处理
  - 被注入 JavaScript 和 CSS 文件等外部资源链接
  - 被注入图标链接
  - 被注入resource hint
  - 被注入manifest
- 可以使用 lodash template语法向该文件插入内容：`<link rel="icon" href="<%= BASE_URL %>favicon.ico">`
- 放置在 public 目录下或通过绝对路径被引用。这类资源将会直接被拷贝，而不会经过 webpack 的处理。
- 在 JavaScript 被导入或在 template/CSS 中通过相对路径被引用。这类引用会被 webpack 处理
