# < meta >

## < meta >简介
- `<meta>`是一个单标签
- `<meta>`标签用于指定文档的元数据.
- 元数据(`metadata`),即描述数据(该文档)的数据。
- `<meta>`标签定义的元数据总是出现在`<head>`标签内。不会显示在前台页面上。
- `<meta>`定义的元数据主要面向浏览器和搜索引擎。
  - 告诉浏览器如何渲染文档
  - 告诉搜索引擎如何检索我(文档的自我介绍)

## < meta >的name属性：面向搜索引擎
- `name`属性用于设置key
  - `keywords`
  - `description`
  - `generator`
  - `author`
  - `application-name`
- `content`属性用于设置value

**定义文档的关键字**

```
<meta name="keywords" content="HTML,CSS,JavaScript">
```
**定义文档的描述**
```
<meta name="description" content="Free Web tutorials">
```

**定义文档的作者**
```
<meta name="author" content="John Doe">
```
**定义文档的编辑器名称**
```
<meta name="generator" content="Dreamweaver">
```
**定义文档的名称**
```
<meta name="application-name" content="Free Tutorials">
```

## < meta >的name属性：面向浏览器
- `name`属性用于设置key：
  - `viewport`
- `content`属性用于设置value：
  - width=device-width (设置视口的宽度为设备的宽度)
  - width=400 (设置视口的宽度为400px)
  - initial-scale=1 (设置viewport的初始缩放比例为1)
  - initial-scale=1.5 (设置viewport的初始缩放比例为1.5)
  - minimum-scale (设置用户的最小缩放度)
  - maximum-scale (设置用户的最大缩放度)
  - user-scalable=yes (允许用户缩放，默认)
  - user-scalable=no (不允许用户缩放)

## < meta >的http-equiv属性：模拟一个HTTP响应头
- `http-equiv`属性用于设置key
- `content`属性用于设置value

**告诉浏览器自动刷新文档**

```
<meta http-equiv="Refresh" content="3"/>
```

**告诉浏览器3秒后自动更新url**

```
<meta http-equiv="refresh" content="3 url=http://www.baidu.com">
```

##  < meta >的charset属性
**告诉浏览器文档的编码**
```
<meta charset='utf-8'>
```
