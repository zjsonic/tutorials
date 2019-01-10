# Console

## Console
- Console是一个对象
- 该对象提供了对浏览器调试控制台的访问
- 不同浏览器，console对象的工作方式有差异


## 访问console对象的方法
- console对象可以从任何全局对象访问
  - Window.console
  - WorkerGlobalScope.console

## console对象的方法
- console.log(information,arg1,arg2...) : 信息的一般输出。可配合参数使用
  - `%d`
  - `%f`
  - `%s`
  - `%o`
```
for(var i=0;i<5;i++){
  console.log('you called %s for %d times','me',i+1)
}
```
- console.dir() : 显示指定对象的属性列表。
  - 使用折叠三角检查子对象的内容。
  - Faded properties apper to indicate non-enumerable properties.
- console.clear() : 清空控制台
