# jQuery for AJAX

## jQuery为AJAX提供了几个方法
-
-
-
-

使用这些方法，你可以请求
- text
- html
- xml
- json

## $().load(url,data,callback)
```
const url = 'https://newsapi.org/v2/everything?q=bitcoin&from=2018-12-12&sortBy=publishedAt&apiKey=ca9b207c09bc4c798e9161e66e1ca133'
$('main').load(url)
```
- 用途：load()方法用于从指定地址请求数据并把数据返回给元素
