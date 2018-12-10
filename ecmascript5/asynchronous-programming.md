# Asynchronous Programming

## JS的call stack
- 当函数调函数的时候,我们需要知道被调用的函数执行完毕后返回到哪.
```
function a(n){
	console.log(n+1) //4. console.log()在函数a的内部开始执行(console.log()位于stack的最顶部) // 5. console.log()执行完毕,返回函数a 6. 函数a执行完毕后返回函数b (函数从stack的最顶部消失)
}

function b(n){
	a(n+1) // 3. 函数a在函数b的内部开始执行(函数a位于stack的最顶部) 7. 函数b执行完毕后返回函数c(函数b从stack的最顶部消失)
}

function c(n){
	b(n+1) //2. 函数b在函数c的内部开始执行(函数b位于stack的最顶部) 8. 函数c执行完毕后,返回全局
}

c(10) //1. 函数c在全局作用域开始执行(函数c位于stack的最顶部)  程序执行的终点
```

## 浏览器的event loop

简单地说，每个浏览器选项卡都在（单个）进程中运行,事件循环执行`任务队列`派发的任务。比如:

- Parsing HTML
- Executing JavaScript code in script elements
- Reacting to user input (mouse clicks, key presses, etc.)
- Processing the result of an asynchronous network request

## WebAPIs
- DOM(events)
- setTimeout/setInterval
- AJAX

