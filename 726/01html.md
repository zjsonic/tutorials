[TOC]

# 认识HTML

## 浏览器是什么

浏览器是解释网页的软件。任何一个浏览器的内部都内置了引擎：

- trident引擎
- Chrome: b-link
- Safari: web-kit 
- 火狐：壁虎

任何一个引擎都可以解释以下三种语言：

- HTML
- CSS
- JavaScript

## 实例演示：创建我的第一个网页

完毕

## 了解什么是HTML?

HTML是英文Hyper Text Markup Language的缩写。翻译成中文，意思是：超文本标记语言。

这种语言用来描述网页的内容（文字、图片、音频、视频等）。**它不关心内容的表现，只关心内容的结构。** 

H: hyper 超

T: Text  文本

M: markup 标记

L：Language 语言

- 交流对象：浏览器
- 背单词
- 记住语法

## 熟记HTML语法

1. 所有的标签都是由尖括号+关键词构成。比如：`<title>`  `</p>` 
   - 关键词：可以是一个单词 也可以是一个字母 
   - 尖括号：必须是英文输入法下的尖括号
2. 所有的标签都是成对出现。比如：`<title> </title>`  
   - 开始标签：`<title>`
   - 结束标签: `</title>` 
3. 所有的标签都有特定的含义。
   - `<p>` 用来定义一个段落。
   - `<h1>` 用来定义一个一级标题。
4. 所有的单标签也必须关闭。
   - `<img />`
5. 所有的标签都必须小写。
6. 所有的标签都具有N种属性。
7. 标签可以嵌套，但必须合理嵌套。
   - 错误：`<h1><p>东方大厦</h1></p>` 
   - 正确：`<h1><p>东方大厦</p></h1>` 


## 掌握20个常见HTML标签

### `<html> </html>` 

- 用途：用来定义一个HTML文档。
- 注意：所有的内容都必须放在`<html>`标签的内部

### `<head>`

- 用途：用来定义一个HTML文档的头部。常用来放置一些关于文档的描述信息，这些信息是提供给开发者或搜索引擎使用的。比如：当前文档的关键词、说明、编辑器、作者、更新时间等等。



### `<body>` 

- 用途：用来定义一个HTML文档的主体。
- 注意：网页中的全部内容都必须放在`<body>`标签的内。



### `<title>`

- 用途：用来定义一个HTML文档的标题。
- 注意：`<title>` 标签必须出现在`<head>` 区域内。



### `<h1>` 

- 用途：用来定义一级标题。
- 注意：`<h1>` 用来定义文章的标题。
- 其他标题标签
  + `<h2>`
  + `<h3>`
  + `<h4>`
  + `<h5>`
  + `<h6>`

### `<p>` 

- 用途：用来定义一个段落。p: paragraph
- 注意：什么才算一个段落？
  + 段落由句子构成。
  + 能表达一个完整的意思就是一个句子。

### `<ul>`

-  UL: unorder list 的缩写   无顺序的列表
- 用途： 用来定义无序列表区域。
- 注意：无序列表不强调顺序。

### `<li>` 

- Li :   list item   列表项
- 用途：用来定义列表项目。
- 注意：该表现必须出现在`<ul>` 或者`<ol>`标签的内部。

### `<ol>`

- Ol:  order list    有序列表
- 用途：用来定义有序列表。
- 注意：有序列表强调顺序。




























