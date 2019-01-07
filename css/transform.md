# Transform

## 用途
- `Transform`属性用于向元素应用2D或3D转换。
- 这种转换(transform)是通过定义css格式化模型中的坐标空间实现的。

## 属性值
- none: 默认值。用于设置无转换。
- transform-functions: 该属性值是一个以空格分隔的转换列表
  - transition():用于转换一个元素的位置。
  - rotate(): 用于旋转一个元素的角度。
  - scale(): 用于缩放一个元素的尺寸。
  - skew(): 用于倾斜一个元素的角度。
  - perspective(): 用于透视一个元素的角度。
- initial
- inherit

## Translate(x,y)
```
.box{
  width:100px;
  height:100px;
  background-color:red;
  transform: translate(100px,100px)
}
```
- x: 代表横坐标。正值向右移动，负值向左移动。
- y: 代表纵坐标。正值向下移动，负值向上移动。
- one value: 代表水平

## roate(Xdeg)
```
.box{
  width:100px;
  height:100px;
  background-color:red;
  transform: rotate(20deg)
}
```
- Xdeg: 代表旋转的角度。
  - 正值clockwise旋转
  - 负值counter-clockwise旋转

## scale()
```
.box{
  width:100px;
  height:100px;
  background-color:red;
  transform:scale(a,b)
}
```
- a代表水平缩放，大于1的的数字代表放大的比例，小于1大于0的数字代表缩小的比例
- b代表垂直缩放，大于1的的数字代表放大的比例，小于1大于0的数字代表缩小的比例
- one-value:代表水平和垂直同时缩放
