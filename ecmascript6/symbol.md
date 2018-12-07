# Primitive value - Symbol 

## Symbol()函数
- Symbol()函数ES6新增的函数
- Symbol()函数是一个特殊的函数
  - 它很想一个内置对象类
  - 它不是一个真正意义上的构造函数,因为它不支持`new Symbol()`
- Symbol()函数返回一个symbol类型的值.
  - 该值具有唯一性
  - 该值可用于对象属性的标识符(这是symbol类型的数据的唯一目的)
- Symbol()的静态属性暴露了几个内置对象
- Symbol()的静态方法暴露了symbol的全局注册

分别创建两个symbol1和symbol2
```
const symbol1 = Symbol()
const symbol2 = Symbol()
console.log(symbol1 === symbol2) //false
```
把symbol1的值复制给symbol2
```
const symbol1 = Symbol()
const symbol2 = symbol1
console.log(symbol1 === symbol2) //true
```

## Symbol([description])语法
`description`: string 对symbol的描述,可用于调试,但不能访问符号本身.

## 创建Symbol原始值
- 使用Symbol()函数创建
- 参数可选
```
var sym1 = Symbol();
var sym2 = Symbol('foo');
var sym3 = Symbol('foo'); 

console.log(sym1) // Symbol()
console.log(sym2) // Symbol(foo)
```

## 为什么不能使用new Symbol
```
var sym = new Symbol(); // TypeError
```
就是为了不让你显式创建Symbol包装对象,我们要创建的是symbol

## Symbol.iterator属性
- 返回值:返回object默认的iterator

## 使用Symbol创建属性名
```

```
