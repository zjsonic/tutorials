# jQuery

## jQuery是什么
jQuery是一个意在改善JavaScript设计模式的库。jQ的主要作为表现在
  - 选择元素
  - 事件处理
  - 动画设计
  - ajax

## 安装JQuery
- 官网下载:[http://jquery.com/download/](http://jquery.com/download/)
```
<script src="./js/jquery.js"></script>
```

## 打印jQuery
```
jQuery = function( selector, context ) {

    // The jQuery object is actually just the init constructor 'enhanced'
    // Need init if jQuery is called (just allow error to be thrown if not included)
    return new jQuery.fn.init( selector, context );
}
```

## 打印jQuery实例对象
```
jQuery.fn.init {}
```

## jQuery库文件的位置
- 必须放置在依赖jQuery的程序之前
- 必须放在任何css样式表文件之后
- 建议在})之后添加一条注释: //end ready

## jQuery的事件函数
- $(document).ready():当文档完全加载完毕时，执行函数
- $().dblclick(handler) 当鼠标双击元素时触发。为元素绑定双击事件
- $().mouseenter(handler) 当鼠标指针进入元素时触发
- $().mousedown(handler) 当按下鼠标时触发
- $().mouseup(handler) 当释放鼠标时触发
- $().mouseleave(handler) 当鼠标离开元素时触发
- $().hover(mouseenter,mouseleave)
- $().focus(handler) 当表单元素拥有焦点时触发
- $().blur(handler) 当表单元素失去焦点时触发
- $().on('eventName',handler) 为元素绑定一个事件处理函数
- $().on({ event1:handler1(){},event2:handler2(){} }) 为元素绑定多个事件处理函数

## jQuery的方法
- 显示隐藏
  - $().hide(speed,callback)
  - $().show(speed,callback)
  - $().toggle(speed,callback)
- 透明度变化
  - $().fadein(speed,callback) fadein()方法允许fade in一个可见元素
  - $().fadeout(speed,callback)  fadeout()方法允许fade out 一个可见元素
  - $().fadetoggle(speed,callback) fadetoggle允许在fadein()和fadeout()之间切换
  - $().fadeto(speed,opacity,callback)  fadeto()方法允许fade to 指定的opacity
- 动画
  - $().animate({options},speed,callback)
    - {options} : 定义动画中用到的css属性
    - 需要手动为元素设置定位属性:relate fixed absolute
    - If you want to animate color, you need to download the Color Animations plugin from jQuery.com
- 操作DOM
  - $().append()
- AJAX
  - $.ajax({options}) //执行异步HTTP
```
$.ajax({
  type: 'GET',
  url: '',
  async: true,
  data: string, //发送到服务器的数据，自动转字符串
  dataType: 'json', //设置响应数据的数据类型
  success(result,status,xhr), //请求成功后的回调函数
  error(xhr,status,error),  //请求失败后的回调函数
  complete(xhr,type), //请求完成后的回调函数
  beforeSend(xhr),
  cache: true
})
```
  - `$().load(url,data,callback)`
    - 用途：load()方法用于从指定地址请求数据并把数据返回给元素
  
