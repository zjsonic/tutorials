# Options Data
- data
- props
- methods
- computed
- watch

## data:Vue实例的数据。
**data is an object**
```
new Vue({
  el: '#app',
  data: {
    firstName: 'Jay',
    lastName: 'Jordan'
  }
})
```
- Vue的data对象必须是纯粹的key/value对（只能是数据，不能有状态）
- Vue把data对象的属性转换为getter和setter，从而让data的属性能够响应数据的变化
- `vm.$data`用来访问原始data对象
- Vue实例代理了data对象的属性，所以`vm.key` = `vm.$data.key`

**data is a function when it used in a component**
```

```


## props:用于接收来自父组件的数据
**props is an Array**


**Porps is an Object**



## methods


## computed

## watch
