[TOC]

# Function

## methods

### Function.call()
A function is called with the give `this` and an argument list.

### Function.apply()
A function is called with the give `this` and an array of arguments.

### Function.bind()
**用途**：`Function.bind()`的方法用于返回一个新函数。
**语法**：`bind(thisArg,arg1,arg2,...,agrN)`

- thisArg: 作为this传递给目标函数
- arg1,arg2,...,argN: 参数列表

示例1：bind()方法可以修改this指向

不同类型的数据：
```
const name = 'zhangsan'
const age = 20
const married = false
const hobbies = ['Swimming','Basketball','Football']
const girl = {
  height: 160,
  edu: '本科'
}
```
函数
```
function person(...arg){
  console.log(this)
  console.log(arg)
}
```
调用bind()方法可以修改指向
```
const p1 = person.bind(girl)  //bind()返回一个绑定函数
p1()  // 之前this指向window,现在this指向girl对象。
```
示例2：调用绑定函数会执行包装函数
```
// person(name)
person.bind(name)() //调用bind()函数会执行包装函数String()
person.bind(age)() //调动bind()函数会执行包装函数Number()
person.bind(married)() //调用bind()函数会执行包装函数Boolean()
```

示例3：绑定函数可以使用new实例化


```
const p = person.bind(girl)
const p1 = new p()
console.log(p1) //实例的原型的constructor指向 person函数
```
示例4： 使用对象的方法创建一个函数，经常会遇到this指向问题
未使用`bind()`
```
const person = {
  age : 30,
  getAge: function(){
    return this.age
  }
}

const getAgeA = person.getAge
console.log(getAgeA()) //undefined
```

使用`bind()`

```
const getAgeB = getAgeA.bind(person)
console.log(getAgeB()) //30
```
示例5：手写一个bind()

手写bind()方法意味着:在Function()构造函数的原型上创建一个新方法
- 目标函数
- 绑定函数：返回的函数
- 参数：obj,...rest,...param
- 创建返回的函数
- 修改绑定函数的原型指向
- 修改绑定函数的原型的constructor

```

const person = function(...args){
  console.log(this)
  console.log(args)
}
person.prototype.aaa = function(){
  console.log('test')
}

    // 1. 目标函数：绑定bind()方法的函数
    // 2. 新函数：bind()方法返回的函数

    //bind()函数的特征
    //1. bind()是定义在Function构造函数上的方法
    //2. bind()的两个参数：thisArg,和args列表,thisArg会替换bind函数调用的主人
    //3. bind()的返回值是一个新函数，新函数执行后，会返回一个值
    //4. bind()新函数是一个构造函数，其原型是目标函数 || customBind()的原型是Function函数

    Function.prototype.customBind = function(thisArg,...args){
      let _this = this
      let newFn = function(){
        _this.apply(thisArg,[...args])
      }
      newFn.prototype = Object.create(_this.prototype)
      newFn.prototype.constructor = _this
      return newFn
    }

console.log('===========返回新函数并不执行==========')
const boundPerson = person.bind({ x: 1 }, 'a','b','c')//返回新函数
const customBoundPerson = person.customBind({ x: 1 }, 'a','b','c')//返回新函数
console.log('===========执行新函数==========')
boundPerson()// this:{ x: 1 },  args:'a','b','c'
customBoundPerson()// this:{ x: 1 },  args:'a','b','c'
console.log('==========创建实例===========')
const instance1 = new boundPerson
console.log(instance1)
const instance2 = new customBoundPerson
console.log(instance2)
console.log('==========查询aaa方法===========')
console.log(instance1.aaa)
console.log(instance2.aaa)
console.log('==========newFN的原型===========')
console.log( boundPerson.__proto__)
console.log(customBoundPerson.prototype)

```
