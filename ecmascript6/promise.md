# Promise

## Promise是什么

- `Promise`是一个构造函数，用于生成promise实例。
    - 该函数的参数是两个内置的方法
        - resolved的作用是将promise对象的状态从pending变成resolved
        - rejected的作用是将proised对象的状态从pending变成rejected
- `Promise`对象保存着一个异步操作的结果。
- 通过对`Promise`对象添加回调函数，可以立刻获得这个结果。
- 有了`Promise`，可以将异步操作以同步操作的流程表达出来，避免层层签套的回调函数。
- 缺点：无法中途取消，一旦创建它就会立刻执行

## promise.then(fb1,fb2)

then方法用来指定promise实例的回调函数：
- fb1: 指定成功状态时的回调函数（接收promise对象传出的值作为参数)
- fb2: 指定失败状态时的回调函数（接收promise对象传出的值作为参数)
```
promise.then(function(value){

},function(error){

})
```