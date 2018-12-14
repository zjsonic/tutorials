# < meta >

## 用途
`<meta>`标签用于指定文档的元数据(metadata，即用于描述数据的数据)。

## < meta >的解析
- 网页中的`metadata`不会显示在页面上
- 网页中的`metadata`会被浏览器解析


## < meta >的类型
- 提供给搜索引擎使用
- 提供给开发者使用

## < meta >的位置
`<meta>`标签总是出现在`<head>`标签内。

## < meta >的语法
- `<meta>`是一个单标签
- `<meta>`在H5中，没有关闭标签。在xhtml中必须关闭
- 总是向`<meta>`中传入一个名值对。

## < meta >的属性

|Attribute|Value|Description|
|-|-|-|
|http-equiv||模拟一个HTTP响应头|
||content-type| 告诉浏览器文档主体内对象的媒体类型|
||default-style|必须匹配同一文档中的一个 link 元素上的 title 属性的值|
||refresh||
|name ||定义文档的关键字描述和viewport等|
||description|定义文档的描述|
||keywords|定义文档的关键字|
||author|定义文档的作者|
||viewport|定义文档的viewport|
||application-name|指定web应用的名称|
|content|text|为`http-equiv`或`name`指定的属性设置值|
|charset|character_set|指定当前文档的字符编码|

## 自动刷新页面
```
<meta http-equiv="Refresh" content="3"/>
```

## 自动跳转
```
<meta http-equiv="refresh" content="3 url=http://www.baidu.com">
```
- `3` : 3秒

## 其他
```
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<meta name="description" content="Free web tutorials">
<meta name="keywords" content="HTML, meta tag, tag reference">
<meta name="application-name" content="W3schools">
<meta name="generator" content="FrontPage 4.0">
<meta name="author" content="John Doe">

<meta http-equiv="content-type" content="text/html charset=utf-8">
<meta http-equiv="default-style" content="the document's preferred stylesheet">
<meta http-equiv="refresh" content="3 url=http://www.baidu.com">
```
