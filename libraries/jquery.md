# jQuery Basic

## 什么是"库"
库就是预先编写好的JS函数的集合.
- 把库引入页面中
- 使用库函数减轻任务复杂程度.

## jQuery是什么
- jQ是一个优秀的js库
- jQ为js提供了一种简便的设计模式
- jQ主要作为表现在
  - 选择元素
  - 事件处理
  - 动画设计
  - ajax
- jQuery是一个构造函数,返回一个jQuery实例化对象.

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
- 在})之后添加一条注释: //end ready



## events
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
- $().hide(speed,callback)
- $().show(speed,callback)
- $().toggle(speed,callback)

- $().fadein(speed,callback) fadein()方法允许fade in一个可见元素
- $().fadeout(speed,callback)  fadeout()方法允许fade out 一个可见元素
- $().fadetoggle(speed,callback) fadetoggle允许在fadein()和fadeout()之间切换
- $().fadeto(speed,opacity,callback)  fadeto()方法允许fade to 指定的opacity


- $().animate({options},speed,callback)
  - {options} : 定义动画中用到的css属性
  - 需要手动为元素设置定位属性:relate fixed absolute
  - If you want to animate color, you need to download the Color Animations plugin from jQuery.com


- $().append()

- $.ajax({options})
```
$.ajax({
  type: 'GET',
  url: '',
  success(result,status,xhr),
  fail(xhr,status,error)
})
```

# jQuery for AJAX

## jQuery为AJAX提供了几个方法
-
-
-
-

使用这些方法，你可以请求
- text
- html
- xml
- json

## $().load(url,data,callback)
```
const url = 'https://newsapi.org/v2/everything?q=bitcoin&from=2018-12-12&sortBy=publishedAt&apiKey=ca9b207c09bc4c798e9161e66e1ca133'
$('main').load(url)
```
- 用途：load()方法用于从指定地址请求数据并把数据返回给元素
