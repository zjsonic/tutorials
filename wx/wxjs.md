# wxjs

## 自定义事件
- 在元素上自定义一个属性
- 在js文件里声明一个方法来响应自定义属性



## page(object)
- 用途：


## app(object)
- 用途：用来注册小程序。
- 参数：
  - ojbect :指定小程序的生命周期回调等。
    - onLaunch(object):小程序初始化完成时触发
    - onShow(object) : 小程序从后台进入前台时触发
    - onHide(): 小程序从前台进入后台时触发
    - onError(stringError):小程序发送脚本错误时触发
    - onPageNotFound(object): 小程序打开的页面不存在时触发
- 语法：
  - `app()`必须在`app.js`中调用。
    - 必须调用
    - 只能调用一次


## getApp(object)
- 用途：获取小程序实例，全局函数。
