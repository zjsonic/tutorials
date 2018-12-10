# Generator函数
- Generator是一种特殊函数
- 定义Generator函数的状态
- 访问Generator函数的状态

## Generator是一种特殊函数

```
function* fn(){ //function后紧跟*定义一个generator函数
	return 'Hello world.'
}

fn() // 返回同名iterator对象
```
1. 定义函数的形式特殊:`function* fn(){}` 星号的意味着该函数不会正常执行,必须遇到.next()方法时才会逐条执行
2. 函数的返回值特殊:返回一个iterator对象,该对象指向函数内部的状态

## 定义Generator函数内部的每个状态
使用`yield`关键词定义
```
const fn = function*(){
	yield 'a'
	yield 'b'
	return 'c'
	yield 'd' // 不会输出
}
```
- yield: 代表输出, 后面的内容可以是任何js表达式
- return: 代表结束,可省略

## 访问Generator函数的内部的状态
调用iterator.next()方法,使得指针指向下一个状态
```
const iterator = fn()
console.log(iterator.next()) //{ value: 'a',done: false}
console.log(iterator.next()) // { value: 'b',done: false }
console.log(iterator.next()) // { value: 'c',done: true }
console.log(iterator.next()) // { value: undefined, done: true }
```
`iterator.next()`方法的返回值是一个拥有`value`和`done`属性的对象


## 为对象添加symbol.iterator属性

对象是没有`symbol.iterator`属性的.使用genrator函数,我们可以为对象添加symbol.iterator属性
```
//为对象添加Symbol.iterator属性

const obj = {}

obj[Symbol.iterator] = function* (){
	yield 1
	yield 2
	yield 3
}

console.log(obj[Symbol.iterator]().next())
```


