# Promise

## Promise是什么
ECMA委员会是这么定义promise：
>A Promise is an object that is used as a placeholder for the eventual results of a deferred (and possibly asynchronous) computation.

- promise是一个对象。
- 该对象起到一个占位符的作用。
- 该占位符是为某个延迟计算(有可能是异步)的最终结果占位。

理解：
- promise是一个容器，里面保存了一个未来才能决定的值。
- 未来值有可能是一个“成功值”，也有可能是一个“失败值”。

这好比：
- 完成一项任务：下个月乘飞机去旅游(乘机任务是一个延迟操作)
- 你预定了一张机票(机票就是promise，先预定一个空位，但下个月能否登上飞机，现在并不确定)
- 你成功登机，你就是那个"成功值"(保存在promise里)。
- 你未成功登机，那么“感冒、堵车”这些导致失败的原因就可以成为“失败值”(保存在promise里)。
- promise只能有一个结果:成功或失败。

## promise语法解析（创建Promise)
- `Promise`是一个构造函数。
- `Promise`参数是一个函数(用于描述要执行的延迟计算)。
  - resolve():为了表示延迟计算成功，我们需要把一个你希望的值(可以是string,number,boolean,object等)传递给resolve函数，该函数会自动把值发送给promise对象(JS引擎内部部署)，这时我们就说`Promise has been resolved`。
  - reject():为了表示延迟计算失败或遇到错误，我们需要把一个值(通常是Error对象)传递给reject函数，该函数会自动把值发送给promise对象(JS引擎内部部署)，这时我们就说`Promise has been rejected`。
  - 注意：并不存在一种事件机制，使得resolve()和reject()函数在延迟计算成功或失败时调用，而是我们需要把他们分别设置在延迟计算成功或失败的逻辑中。
  - 特点：固定性，状态一旦变化，永远不会改变。因此有了`Promise`，可以将异步操作以同步操作的流程表达出来，避免层层签套的回调函数。
  - 缺点：无法中途取消，一旦创建它就会立刻执行

## promise.then(callback1,callback2)(使用Promise)
获取promise对象中保存的值：
```
promise.then(function(value){

},function(error){

})
```
- `then(callback1,callback2)`:指定promise实例的回调函数：
- 参数：
    - callback1(onResolved): 当promise为resolved时调用。
        - 返回一个新的promise实例（需要手动设置return)
    - callback2(onRejected) 可选。当promise为rejected时调用。
        - 
- 返回值：第一个回调函数

## promise.catch(onRejected)
Since error handling is a necessity for robust programs, a shortcut is given for such a case. Instead of writing .then(null, () => {...}) when we want to handle an error, we can use .catch(onRejected) which accepts one callback: onRejected.
Remember that .catch is just a syntactical sugar for .then(undefined, onRejected).

## Chaining promises(链式Promises)
.then() and .catch() methods always return a promise. So you can chain multiple .then calls together. Let’s understand it by an example.

First, we create a delay function that returns a promise. The returned promise will resolve after the given number of seconds. Here’s its implementation —

```
const delay = (ms) => new Promise(
  (resolve) => setTimeout(resolve, ms)
);

delay(2000)
  .then(() => {
    console.log('Resolved after 2 seconds')
    return delay(1500);
  })
  .then(() => {
    console.log('Resolved after 1.5 seconds');
    return delay(3000);
  }).then(() => {
    console.log('Resolved after 3 seconds');
    throw new Error();
  }).catch(() => {
    console.log('Caught an error.');
  }).then(() => {
    console.log('Done.');
  });

// Resolved after 2 seconds
// Resolved after 1.5 seconds
// Resolved after 3 seconds
// Caught an error.
// Done.
```


## 参考
- [https://codeburst.io/a-simple-guide-to-es6-promises-d71bacd2e13a](https://codeburst.io/a-simple-guide-to-es6-promises-d71bacd2e13a)