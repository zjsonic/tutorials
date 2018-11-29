# URL Module
- 简介
- URL字符串和URL对象
- URL API
- Legacy URL API
- Percent-Encoding in URLs

## URL Module简介
`url`模块提供了解析url的实用功能。
```
https:   //    user   :   pass   @ sub.example.com : 8080   /p/a/t/h  ?  query=string   #hash
```


## URL字符串
URL字符串是包含多个有意义的组件的结构化字符串。解析后，将返回一个URL对象，其中包含这些组件的每个属性。

## URL对象


- url.href:Gets and sets the serialized URL
- url.protocol
- url.username
- url.password
- url.host
- url.hostname
- url.port
- url.pathname
- url.search :获取或设置URL的序列化查询部分
- url.hash

## url.parse(url,[parseQueryString,[slashesDenoteHost]])
url.parse()方法获取一个URL字符串，对其进行解析，然后返回一个URL对象。