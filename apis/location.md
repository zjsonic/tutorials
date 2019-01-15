# Location

## Location对象的打印

![location object](images/location-object.png)


## Location对象简介
- `location`对象表示当前窗口载入的文档的`url`。
- `window.location`表示对`location`对象的动态引用。
- `window.document.location`表示对`location`对象的静态引用。

## location对象的属性
- `location.href` :返回`url`的完整字符串
- `location.protocol`: 返回`url`协议字符串(包括冒号在内)
- `location.host`: 返回url的`域名`+`:`+`port`
- `location.hostname`: 返回url的`域名`
- `location.port` : 返回url的`端口号`
- `location.pathname`: 返回url的路径
- `location.search`: 返回以问号开头的查询字符串
- `location.hash`:返回以井号开头的片段标识符

## location对象的方法
- `location.assign()`: 载入指定的url
- `location.replace()`: 使用指定的url替换当前url
- `location.reload()`: 重新载入指定的url
- `location.toString()`: 转换location对象为字符串
