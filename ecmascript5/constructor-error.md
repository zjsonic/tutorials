# Error构造函数
通过`Error`构造函数可以创建一个错误对象，当程序运行出错时，程序会停止执行，并抛出`Error`的实例。该实例对象包含了错误的名称和提示信息。

## Error对象的属性
- `error.name`:设置错误的名字/返回错误的名字
 - `Error` error实例的默认名字
 - `ReferenceError` 非法引用错误
 - `SyntaxError` 语法错误
 - `TypeError` 类型错误
 - `RangeError` 使用内置对象的方法时，参数超范围
 - `URIError` 编码错误（encodeURI()、decodeURI()、encodeURIComponent()、decodeURIComponent()、escape()和unescape()这六个函数）
 - `EvalError` eval()函数未被正确执行
- `error.message`:string 设置错误的提示信息/返回错误的提示信息

## Throw Error
`throw Error`:当错误出现，js通常会停止执行并生成一个错误消息。实际上，js会使用`error.name`和`error.message`创建一个`Error`对象。
```
Uncaught ReferenceError: a is not defined at index.html:8
```
```
Uncaught SyntaxError: Unexpected token }
```

## try语句
- try用于定义一段代码测试潜在的错误。
- 无参数

## catch(error)语句
- 当try语句中出现错误时，使用catch语句处理错误
- try和catch是成对出现的
- try语句测试无错误，则catch代码块不执行
- try语句测试出现错误，则执行catch代码块


## finally语句
- finaly用于处理代码块中潜在的错误。

## throw语句
- throw语句允许你创建自定义错误。
- error可以是：
 - String
 - Number
 - Boolean
 - Object
- 配合try/catch语句，可以控制程序流，创建自定义错误消息
```
console.log('hello')
throw 'This is an error.' // return 'Uncaught This is an error.' 停止程序继续执行
console.log('world')
```
```
console.log('hello')
throw new Error() // return Error 停止程序继续执行
console.log('world')
```

- ReferenceError子类
- TypeError子类
- RangeError子类
- SyntaxError子类
- EvalError子类
- URIError子类

## 定义
`Error`对象在出现错误的时候，负责提供错误信息。

## error Object的属性
## error.name
用途：设置或返回`error`的名字。
### error.message
用途：设置或返回`error`的信息（字符串形式)。

## 实例
```
<p id="demo" style="color:red"></p>

<script>
try {
    adddlert("Welcome guest!");
}
catch(err) {
    document.getElementById("demo").innerHTML =
    err.name + "<br>" + err.message;
}
</script>
```




## try/catch/finally Statement
### 定义
try/catch/finaly用于处理代码块中潜在的错误。
- try语句 : 定义测试的代码块。
- catch语句 : 定义处理错误的代码块。
- finaly语句 : 定义出现错误后执行的代码。
```
try {
    tryCode - Block of code to try
}
catch(err) {//err作为变量参数会引用 error Object
    catchCode - Block of code to handle errors
}
finally {
    finallyCode - Block of code to be executed regardless of the try / catch result
}
```

### 实例

```
function myFunction() {
    var message, x;
    message = document.getElementById("message");
    message.innerHTML = "";
    x = document.getElementById("demo").value;
    try {
        if(x == "") throw "is Empty";
        if(isNaN(x)) throw "not a number";
        if(x > 10) throw "too high";
        if(x < 5) throw "too low";
    }
    catch(err) {
        message.innerHTML = "Input " + err;
    }
}
```

```
function myFunction()
    var message, x;
    message = document.getElementById("message");
    message.innerHTML = "";
    x = document.getElementById("demo").value;
    try {
        if(x == "") throw "Empty";
        if(isNaN(x)) throw "Not a number";
        if(x > 10) throw "Too high";
        if(x < 5) throw "Too low";
    }
    catch(err) {
        message.innerHTML = "Error: " + err + ".";
    }
    finally {
        document.getElementById("demo").value = "";
    }
}
```
