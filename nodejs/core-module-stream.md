# Stream Module
- 打印Stream Module
- Stream Module简介
- stream的类型
- API for Stream Consumers
    - Writable Streams
    - Readable Streams
    - Duplex and Transform Streams
    - stream.finished(stream[, options], callback)
    - stream.pipeline(...streams, callback)
- API for Stream Implementers
    - Simplified Construction
    - Implementing a Writable Stream
    - Implementing a Readable Stream
    - Implementing a Duplex Stream
    - Implementing a Transform Stream
- Additional Notes

## 打印Stream Module

## Stream Module简介
- `stream`是一个抽象的接口，用于处理Node.js中的流数据。
- `stream`模块提供了一个基本API，可以轻松构建实现流接口的对象。
- Node.js提供了许多流对象。 例如，对HTTP服务器和process.stdout的请求都是流实例。
- Streams can be readable, writable, or both. All streams are instances of EventEmitter.


