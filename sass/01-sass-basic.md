# Sass Basic
- installation
- preprocess
- watch
- variables
- nesting
- partials
- import
- mixins
- inheritance
- operators

## 什么是Sass
- Sass是CSS的元语言.
- 用于描述CSS语言.
- Sass是css的预处理器

## installation
Install Anywhere
```
npm install -g sass
```
Install on MacOX
```
brew install sass/sass/sass
```

## Preprocess(预处理)
Preprocess refers to compling your Sass to CSS using the `Sass` command.
You'll need to tell Sass which file to build from and where to output CSS to.
```
sass input.scss  output.css
```

## watch(监听)
You can watch and output to the specified directories
```
sass --watch sass:css
```
sass would watch all the files in the sass folder for changes,and compile CSS to the css folder

## variables(变量)
Variables is the way to sore information that you want to reuse.You can sore things like:
- colors
- font stack
- any css value you wanna reuse
Sass uses the `$` to make something a variable.Here's an example:
```
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body{
    font: 100% $font-stack;
    color: $primary-color;
}
```
在处理Sass文件的时候,编译器会输出普通的css,并使用变量值替换掉变量.

## Nesting(嵌套)
- 在Sass中,CSS选择器可以嵌套使用
- css选择器的签套规则:参照HTML的嵌套结构
- 过度嵌套css选择器可导致难以维护
```
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```
## Partials(模块)
partials Sass可以看做是Sass的模块.
- Sass允许把经常复用的代码单独写在一个文件中,然后通过`@import`指令导入到文件中
- 该文件的名字必须是`_`开头, 如:`_nav.scss`.`_`告诉processer,不要把我生成css文件.

## @Import(导入)
- CSS语法中可使用`@import`指令可以引入外部css模块文件.缺点就是每次会创建一个HTTP请求
- Sass构建在CSS的`@import`指令之上,但不需要HTTP请求.Sass将获取您要导入的文件并将其与您导入的文件合并，这样您就可以将单个CSS文件提供给Web浏览器。
例如:We want to import `_reset.scss` into `base.scss`.

`_reset.scss`

```
html,
body,
ul,
ol {
  margin:  0;
  padding: 0;
}
```
base.scss
```
@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```
## Mixins(组合)

在写css代码的过程中,有些时候回很乏味,比如css3的厂家前缀.
Sass的`Mixins`允许你创建一组css声明,甚至可以传入值.
关于Mixins最适合构建vendor prefixes
sass
```
@mixin transform($property) {
  -webkit-transform: $property;
  -ms-transform: $property;
  transform: $property;
}

.box { @include transform(rotate(30deg)); }
```

css
```
.box {
  -webkit-transform: rotate(30deg);
  -ms-transform: rotate(30deg);
  transform: rotate(30deg);
}
```

## @extend/inheritance
- `@extend`是Sass最有用的功能之一。
- `@extend`可以将某个选择器的一组CSS属性扩展到另一个选择器中。
- 它有助于保持你的Sass非常干燥。
最好的应用案例是:创建消息模块
- 错误
- 警告
- 成功
sass
```
/* This CSS will print because %message-shared is extended. */
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

// This CSS won't print because %equal-heights is never extended.
%equal-heights {
  display: flex;
  flex-wrap: wrap;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}

.warning {
  @extend %message-shared;
  border-color: yellow;
}
```
css
```
/* This CSS will print because %message-shared is extended. */
.message, .success, .error, .warning {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```
## Operators
Sass提供了5个数学运算符用于数学计算.
- `+`
- `-`
- `*`
- `/`
- `%`
sass
```
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}
```
css
```
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 62.5%;
}

aside[role="complementary"] {
  float: right;
  width: 31.25%;
}
```



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
To create a mixin you use the @mixin directive and give it a name. We've named our mixin transform. We're also using the variable $property inside the parentheses so we can pass in a transform of whatever we want. After you create your mixin, you can then use it as a CSS declaration starting with @include followed by the name of the mixin.
