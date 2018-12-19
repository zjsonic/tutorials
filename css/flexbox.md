# Flexbox详解

- 如果不了解CSS布局的知识，请点这里：[《CSS的布局模型》](css-layout.md)
- 本文编写基于CSS-tricks的文章（[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)）和我自己的理解。如果错误请指正。

## 常规布局
常规布局指基于`block`或`inline-blok`的布局
- flow
- float
- position

常规flow布局:

![流动布局下的四个div元素](images/flexbox01.png)

HTML代码：
```
<body>
    <div class="container">
      <div class="item1">A</div>
      <div class="item2">B</div>
      <div class="item3">C</div>
    </div>
</body>
```

CSS代码：
```
<style>
  .container{
      max-width:1000px;
      height:500px;
      margin: 0 auto;
      border:1px solid #ccc;
      background-color: #eee;
  }
  .item1{
    width:50px;
    height:200px;
    background-color:red;
  }
  .item2{
    width:100px;
    height:100px;
    background-color:green;
  }
  .item3{
    width:200px;
    height:50px;
    background-color:blue;
  }
</style>
```

## 常规布局特征
- 元素的尺寸不可自动改变
- 元素的排列与方向有关
  - 块元素：自上而下排列
  - 内联元素：自左而右排列

## flexbox布局特征：
- 元素的尺寸可自动改变
- 元素的排列与方向无关
  - 子元素：在水平垂直方向上可任意排列

## flexbox的几个基本概念：
|概念|说明|概念|说明|
|-|-|-|-|
|flex container| 父元素|||
|flex items| 子元素|||
|main axis|主轴(子元素排列参照的轴)|cross axis|垂直轴(与当前主轴垂直的轴)|
|main start|子元素排列的起点(主轴方向)|cross start|子元素排列的起点(垂直轴方向)|
|main end|子元素排列的终点(主轴方向)|cross end|子元素排列的终点(垂直轴方向)|
|main size|父元素尺寸(主轴方向)|cross size|父元素尺寸(垂直轴方向)|

## display:flex (父元素属性)
效果：
![重置父元素的display属性值为flex](images/display-flex.png)

CSS：
```
.container{
  display: flex;
}
```
为父元素设置`display:flex`后，发生了哪些事情？
- 取消了父元素(`.container`)上的流动布局模型
- 在父元素上建立了flex布局模型
  - 建立了flex-container和flex-items
  - 建立了main-axis和cross-axis
  - 建立了start和end
  - main-size由width或height决定
  - cross-size由height或width决定


## display:inline-flex(父元素属性)
效果：
![重置父元素的display属性值为inline-flex](images/display-inline-flex.png)

CSS：
```
.container{
  display: inline-flex;
}
```
为父元素设置`display:flex`后，发生了哪些事情？
- 取消了父元素(`.container`)上的流动布局模型
- 在父元素上建立了flex布局模型
  - 建立了flex-container和flex-items
  - 建立了main-axis和cross-axis
  - 建立了start和end
  - **main-size不再由width或height决定，而是由子元素的宽度之和决定（换言之，父元素像内联元素一样，具有向内收缩适应内容宽度的特性）**
  - cross-size依然由height或width决定


## flex-direction:row
效果：
![flex-direction:row](images/flex-direction-row.png)

CSS：
```
.container{
  flex-direction: row;
}
```

## flex-direction:row-reverse
效果：
![flex-direction:row-reverse](images/flex-direction-row-reverse.png)

CSS：
```
.container{
  flex-direction: row-reverse;
}
```

## flex-direction:column
效果：
![flex-direction:column](images/flex-direction-column.png)

CSS：
```
.container{
  flex-direction: column;
}
```

## flex-direction:column-reverse
效果：
![flex-direction:column-reverse](images/flex-direction-column-reverse.png)

CSS：
```
.container{
  flex-direction: column-reverse;
}
```



## flex-wrap: 规定父元素是否允许子元素换行
属性值：
- nowrap
- wrap
- wrap-reverse

默认值`nowrap`的效果 (主轴方向为水平)
![默认状态下，flex-wrap的值为nowrap](images/flexbox04.png)

CSS代码：
```
.container{
  flex-direction: row;
  flex-wrap: nowrap;
}
```

设置为`wrap`的效果(主轴方向为水平)
![设置flex-wrap的值为wrap的效果](images/flexbox05.png)

CSS代码：
```
.container{
  flex-direction: row;
  flex-wrap: wrap;
}
```
默认为`nowrap`的效果(主轴方向为垂直)
![默认状态下，flex-wrap的值为nowrap](images/flexbox06.png)
CSS代码：
```
.container{
  flex-direction: column;
  flex-wrap: nowrap;
}
```

设置为`wrap`的效果(主轴方向为垂直)
![设置flex-wrap的值为wrap的效果](images/flexbox07.png)

CSS代码：
```
.container{
  flex-direction: column;
  flex-wrap: wrap;
}
```






## Flexbox布局的目标
提供一种更 **有效** 的布局方式。
- 在一个容器内
- 分配空间
- 对齐元素
- 即使元素的尺寸未知或是动态的

## Flexbox实现的思想
赋予父容器一种 **控制子元素尺寸** （意味着分配剩余空间）的能力。
- 主轴为横轴时：子元素的width受父元素控制，height不受父元素控制
- 主轴为纵轴时：子元素的height受父元素控制，width不受父元素控制


## Flexbox的特点
- 方向不固定:传统的布局(块垂直排列 inline水平排列)缺乏灵活性
- flexbox是一个模块，而非一个属性，是一整套属性


## Terminology
- flex container : 父元素
- flex items： 子元素
- main axis : flex items排列参照的轴。取决于`flex-direction`属性
- main start: flex items排列的起点
- main end: flex items排列的终点
- main size: flex items的width或height
- cross axis: 与main axis 垂直的轴叫cross asis
- cross start: flex lines堆积的起点
- cross end: flex lines堆积的终点
- cross size: flex items的height或width

## container的属性
|序号|property|描述|属性值|
|-|- | - | - |
|1|display|定义flex container。为所有直接子元素激活弹性环境。|`flex` `inline-flex`|
|2|flex-direction|建立主轴|`row` `row-reverse` `column` `column-reverse`|
|3|flex-wrap|flex items是否换行|`nowrap` `wrap` `wrap-reverse`|
|4|justify-content|沿主轴分配空间(元素之间的空间）|`flex-start` `flext-end` `center` `space-between` `space-arountd` `space-evenly`|
|5|align-content|沿纵轴分配空间（行之间的空间，单行无效）|`flex-start` `flex-end` `center` `space-between` `space-around` `stretch`|
|6|align-items|沿纵轴分配空间(单行有效）|`flex-start` `flex-end` `center` `stretch` `baseline`|

- `column`属性对flex container无效

## items的属性
|序号|property|描述|属性值|
|-|- | - | - |
|1|order|控制items的排列顺序|integer：默认为0，负值有效|
|2|flex-grow|分配剩余空间给谁|number：默认为0,负值无效|
|3|flex-shrink|收缩元素|number:默认为0,负值无效|
|4|flex-basis|定义元素的基尺寸|默认为auto:依照width和height content:依照内容 长度值 关键词|
|5|align-self|覆盖align-items的属性，为单个元素设置|`flext-start` `flex-end` `center` `stretch` `baseline`|

```
<style>
        .container{
            max-width:1000px;
            height:500px;
            margin: 0 auto;
            border:1px solid #ccc;
            background-color: #eee;
            /* 激活flex context。 */
            display: flex;
            /* 建立主轴：row(default) row-reverse column column-reverse */
            flex-direction:row;
            /* 控制换行:nowrap(default) wrap wrap-reverse(沿纵轴逆向排列) */
            flex-wrap:wrap;
            /* 沿主轴分配空间 flex-start */
            justify-content:flex-start;
            /* 沿纵轴分配空间 flex-start */
            align-content:flex-start;
            /* 沿纵轴分配空间 flex-start */
            align-items: flex-end;
        }
        .items{
            flex-basis:0;
            /* height:98px; */
            background-color:red;
            border:1px solid black;
            flex-grow:1;
            /* flex-shrink:.3 */

        }
        .item1{
            flex-grow:.3
            /* flex-shrink:2 */

        }
        .item2{
            flex-grow:.5;
            align-self:flex-start;
        }
        .item3{
            flex-grow:.2;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="items item1">A</div>
        <div class="items item2">B</div>
        <div class="items item3">C</div>
        <!-- <div class="items item4">D</div>
        <div class="items item">E</div>
        <div class="items item">F</div>
        <div class="items item">G</div>
        <div class="items item">H</div>
        <div class="items item">I</div>
        <div class="items item">G</div>
        <div class="items item">I</div>
        <div class="items item">G</div>
        <div class="items item">I</div>
        <div class="items item">G</div> -->
    </div>
</body>
```

## 参考
- [css-tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
