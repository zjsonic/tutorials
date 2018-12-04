# Error构造函数
通过`Error`构造函数可以创建一个错误对象，当程序运行出错时，程序会停止执行，并抛出`Error`的实例。该实例对象包含了错误信息(错误的名称和提示信息)。

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
```
try{
    //code
}
```
- try用于定义一段测试潜在错误的代码。
- 无参数
- 注意：**try只能测试运行阶段出现的错误，如果是解析阶段出现的语法错误是try不到的**。

## catch(error)语句
```
catch(error){
    //code
}
```
- 当try语句中出现错误时，使用catch语句处理错误
- try和catch是成对出现的
- try语句测试无错误，则catch代码块不执行
- try语句测试出现错误，则执行catch代码块
```
 try{
// say('Hi,Good morning.')  // caught: ReferenceError: say is not defined.
// say // caught: ReferenceError: say is not defined.
// const say //Uncaught SyntaxError: 该错误在解析阶段出现，非运行阶段出现，所以try不到
throw 'fdsafsafsafsa' //caught: 'fdsafsafsafsa'
} 
catch(err){
alert(err) 
}

```


## finally语句
- 语法
```
finally{
    //code...
}
```
- Finally语句允许您在TRY和CATCH语句之后执行代码，而不管TRY和CATCH语句执行的结果如何。

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
throw new Error() // return 'Uncaught Error at index.html:19' 停止程序继续执行
console.log('world')
```


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
