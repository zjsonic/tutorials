## install mongoose
```
npm install --save mongoose
```

## mongoose()
- 用途：`mongoose`是一个构造函数
- 参数：
- 返回值：`mongoose`模块的输出对象是`mongoose`类的一个实例。（大多时候只引用这个实例即可）

## mongoose.prototype.connect()
- 用途：打开默认的`mongoose连接`(数据库)
- 参数
  - uri
  - options
  - callback
- 返回值：Promise

## Mongoose.prototype.Schema(definition,[options])
- 用途：schema()是一个构造函数，用于创建数据模式。
- 参数
    - definition: object 定义模式
- 返回值：
- Schema.Types
 - String
 - Number
 - Boolean
 - Array
 - Buffer
 - Date
 - ObjectId
 - Mixed

## Mongoose.prototype.model(name,[schema],[collection],[skipInit])
- 用途：Defines a model or retrieves it.Models defined on the mongoose instance are available to all connection created by the same mongoose instance.
- 参数：
 - name: string/function  模型的名字

## Model.prototype.save()
- 用途：保存模型文档
- 返回值：undefined/promise

## mongoose.prototype.connection()
- 用途：默认情况下，该连接用于每一个使用`mongoose.model`创建的model
- 参数
- 返回值 ： connection (mongoose模块的默认连接)

## mongoose.prototype.model()
- 用途:
  - 定义model|检索model
  - 定义在mongoose实例上的所有models对所有使用同一个mongoose实例创建的连接来说，都是可用的。
- 参数
  - name(string|function)
  - schma(schema)
  - collection：(string)从model名称获取的名字
  - skipInit(false/true):是否跳过初始化
- 返回值: model


## 打印mongoose
```
Mongoose {
  connections: 
   [ NativeConnection {
       base: [Circular],
       collections: {},
       models: {},
       config: [Object],
       replica: false,
       options: null,
       otherDbs: [],
       relatedDbs: {},
       states: [Object],
       _readyState: 0,
       _closeCalled: false,
       _hasOpened: false,
       '$internalEmitter': [Object],
       _listening: false } ],
  models: {},
  modelSchemas: {},
  options: { pluralization: true },
  _pluralize: [Function: pluralize],
  plugins: 
   [ [ [Function], [Object] ],
     [ [Function], [Object] ],
     [ [Object], [Object] ],
     [ [Function], [Object] ] ] }

```