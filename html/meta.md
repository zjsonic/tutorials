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
|http-equiv||为浏览器指定HTTP头字段|
||content-type| 告诉浏览器文档主体内对象的媒体类型|
||default-style||
||refresh||
|name ||定义文档的关键字描述和viewport等|
||description|定义文档的描述|
||keywords|定义文档的关键字|
||author|定义文档的作者|
||viewport|定义文档的viewport|
||application-name|指定web应用的名称|
|content|text|为`http-equiv`或`name`指定的属性设置值|
|charset|character_set|指定当前文档的字符编码|
