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

