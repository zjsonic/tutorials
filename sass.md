[TOC]

# SASS

Sass is the most mature, stable and powerful professional grade CSS extension language.

- CSS is getting larger, more complex, and hard to maintain. 
- Sass can help. Features that don't exist in CSS: 
  + variables
  + nesting
  + mixins
  + inheritance

## Install Sass

### Standalone Installation

On Windows, Mac and Linux, you can install sass by downloading the package from [github](https://github.com/sass/dart-sass/releases/tag/1.22.1) and adding it to your path: (Mac OS X )

1. Open the *.**bash_profile* file in your home directory (for example, /Users/your-user-name/*.**bash_profile*) in a text editor.
2. Add export PATH="your-dir:$PATH"to the last line of the file,where your-dir is the directory you want to add. 
3. Save the *.**bash_profile* file. 
4. Restart your terminal.

### Installation with NPM

```bash
npm install -g sass
```

### Installation with applications

- compass.app
- koala
- GhostLab

## Compiling Sass To CSS

### Using the sass command

```bash
sass ./css/input.scss  ./css/output.css
```

You can `watch`  and `output`  to the specified directories

```bash
sass --watch ./scss:./css
```
sass would watch all the files in the sass folder for changes,and compile CSS to the css folder.

### Using Plugins

- VS code extensions: Live Scss Compiler
  + Click to `Watch Scss` button from the status bar.

## variables
Variables is the way to sore information that you want to reuse throughout your stylesheets. You can sore things like:
- colors
- font stack
- any css value you wanna reuse

to make something a variable, you can use the `$` .

```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body{
    font: 100% $font-stack;
    color: $primary-color;
}
```
## Nesting

HTML has a clear nested structure. On the other hand, CSS doesn't. 

Sass allows you to nest CSS selectors in a way that follows the same structure of your HTML. Be aware of overly nested rules.

```scss
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


