# CSS3

## Summary
Cascading Style Sheets (CSS) is a style sheet language used for describing the look and formatting of a document written in a markup language. CSS3 is a latest standard of css earlier versions(CSS2). The main difference between css2 and css3 is follows −

- Media Queries
- Namespaces
- Selectors Level 3
- Color

## CSS3 modules
CSS3 is collaboration of CSS2 specifications and new specifications, we can called this collaboration is module. Some of the modules are shown below −

- Selectors 选择器
- Box Model 盒模型
- Backgrounds 背景
- Image Values and Replaced Content 图片值和可替换内容
- Text Effects 文本效果
- 2D Transformations 2D变换
- 3D Transformations 3D变换
- Animations 动画
- Multiple Column Layout 多列布局
- User Interface 用户界面

## border-radius
1. 用途
	- 为元素设置圆角。
	- 定义元素的圆角半径
2. 语法格式
```css
选择器{border-radius:20px 30px 40px 50px}
选择器{border-radius:10% 20% 30% 40%;}
选择器{border-radius:20px|50%;}
```
3. 设置圆角的三种元素
- an element with a specified background color.
- an element with a border
- an element with a background image

4. 圆角属性组
- border-radius
- border-top-left-radius
- border-top-right-radius
- border-bottom-right-radius
- border-bottom-left-raidus


## border-image-source
1. 用途：定义边框图像源。
2. 语法：
```css
selector{
	border-image-source:url();
}
```
3. 属性值
## border-image-slice
1. 用途：定义从哪里切割边框图像。(图形被分割成9个部分：four-corners,four-edges,the middle.)
2. 语法：
```css
selector{
	border-image-slice:number|%|fill;
}
```
3. 属性值
- number: 从指定的数值位置开始切图
	* 位图：数字表示像素
	* 矢量图：数字表示坐标
- %: 从指定的百分比位置开始切图
- fill:The "middle" part is treated as fully transparent, unless the fill keyword is set.

## border-image-repeat
1. 用途：指定边框图像的重复方式。
2. 语法：
```css
selector{
	border-image-repeat:stretch(default) | repeat | round;
}
```
3. 属性值
- number: 从指定的数值位置开始切图
	* 位图：数字表示像素
	* 矢量图：数字表示坐标
- %: 从指定的百分比位置开始切图
- fill:The "middle" part is treated as fully transparent, unless the fill keyword is set.

## border-image
1. 用途：A shorthand property for the 5 individual properties.
2. 语法格式
```css
selector{
	border-image: url() 33% round;
}
```
## background-image
1. 用途：为元素设置一张或多张背景图像。
2. 语法
```css
selector{
	background-image: url(), url(),...,url();
}
```
## background-image
1. 用途：为元素设置渐变背景。
2. 语法
```css
selector{
	background-image: linear-gradient()｜radial-gradient()｜repeating-linear-gradient()｜repeating-radial-gradient();
}
``` 
3. 属性值
- linear-gradient()
- radial-gradient()
- repeating-linear-gradient()
- repeating-radial-gradient()
## background-origin
1. 用途：指定背景图像的定位参照物。
2. 语法
```css
selector{
	background-orgin: content-box|padding-box|border-box;
}
``` 
3. 属性值
- content-box
- padding-box
- border-box

## background-size
1. 用途：指定背景图像的尺寸。
2. 语法
```css
selector{
	background-size: auto|length|cover|contain;
}
``` 
3. 属性值
- auto:Default value. The background image is displayed in its original size.
- length: The background image is displayed in the size you set. The first value sets the width. The second value sets the height. If only one value is given, the second is set to 'auto'.
- percentage:Sets the width and height of the background image in percent of the parent element.
- cover: Resize the background image to cover the enter container.
- contain:Resize the background image to make sure the image is fully visible.

## background-clip

1. 用途：指定背景图像或背景色如何在图像内延伸。
2. 语法
```css
selector{
	background-clip: border-box|padding-box|content-box;
}
``` 
3. 属性值
- border-box:
- padding-box
- content-box

## color属性值
CSS3支持：
- 140+种颜色名称
- HEX values
- rgb(red, green, blue)
- rgba(red, green, blue, alpha)
	* alpha: 0 - 1 
- hsl(hue, saturation, lightness)
	* hue: 0 - 360 
	* saturation: 0 -100%
	* lightness: 0 -100%
- hsla(hue, saturation, lightness,alpha)
	* alpha: 0 - 1  
- opacity
	- 0.1 - 1.0 

## box-shadow
1. 用途：向元素添加一个或多个阴影。
2. 语法
```css
selector{
	box-shaodw: none|h-offset v-offset blur-radius spread color; 
}
``` 
3. 属性值
- none：Default value. No shadow
- h-offset: required,a positive/negative value
- v-offset: required,a positive/negative value
- blur-radius: The blur radius. The higher the number, the more blurred the shadow will be
- spread:The spread radius. A positive value increases the size of the shadow, a negative value decreases the size of the shadow
- color:The color of the shadow. The default value is the text color.



## text-shadow
1. 用途：向文本添加一个或多个阴影。
2. 语法
```css
selector{
	text-shaodw: none|h-offset v-offset blur-radius color; 
}
``` 
3. 属性值
- none：Default value. No shadow
- h-offset: required,a positive/negative value
- v-offset: required,a positive/negative value
- blur-radius: The blur radius. The higher the number, the more blurred the shadow will be
- color:The color of the shadow. The default value is the text color.

## box-sizing属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值
- content-box: Default. The width and height properties (and min/max properties) includes only the content. Border and padding are not included
- border-box: The width and height properties (and min/max properties) includes content, padding and border

## @font-face选择器
1. 用途：允许设计师使用特殊字体。
2. 语法
```css
@font-face{
	font-family; 
	src:;
	font-style:;
	font-weight:;
	font-stretch:;
}
``` 
3. 属性
- font-family: 设置字体名称;
- src: 指定字体文件的url
- font-style: 指定字体风格
- font-weight: 指定字重
- font-stretch: 指定字体拉伸方式

## 2D transform属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## 3D transform属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## transition属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## @keyframes规则
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## animation-name属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## animation-duration属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## animation-delay属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## animation-timing-function属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值
- 
## animation-iteration-count属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## animation-direction属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## animation-fill-mode属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值

## animation属性
1. 用途：指定元素尺寸的计算方式。
2. 语法
```css
selector{
	box-sizing:content-box|border-box; 
}
``` 
3. 属性值
- 






## cal()
1. 用途：生成一个计算值。
2. 语法
```css
selector{
	width:cal(100% - 50px)
}
```
3. 属性值
- expression：equired. A mathematical expression. The result will be used as the value. The following operators can be used: + - * /

## CSS Functions

|Function|Description|
|-|-|
|attr()|	Returns the value of an attribute of the selected element|
|calc()	|Allows you to perform calculations to determine CSS property values|
|counter()|	Returns the current value of the named counter|
|cubic-bezier()	|Defines a Cubic Bezier curve|
|hsl()	|Defines colors using the Hue-Saturation-Lightness model (HSL)|
|hsla()|	Defines colors using the Hue-Saturation-Lightness-Alpha model (HSLA)|
|linear-gradient()	|Sets a linear gradient as the background image. Define at least two colors (top to bottom)|
|radial-gradient()	|Sets a radial gradient as the background image. Define at least two colors (center to edges)|
|repeating-linear-gradient()	|Repeats a linear gradient|
|repeating-radial-gradient()	|Repeats a radial gradient|
|rgb()	|Defines colors using the Red-Green-Blue model (RGB)|
|rgba()|	Defines colors using the Red-Green-Blue-Alpha model (RGBA)|
|var()	|Inserts the value of a custom property|

## Variations
- CSS was first proposed by Håkon Wium Lie on October 10, 1994
- the first W3C CSS Recommendation (CSS1)[24] being released in 1996 
- CSS level 2 specification was developed by the W3C and published as a recommendation in May 1998. 
- After being reviewed by the W3C Advisory Committee, it was finally published as a W3C Recommendation on 7 June 2011.
- Unlike CSS 2, which is a large single specification defining various features, CSS 3 is divided into several separate documents called "modules". Each module adds new capabilities or extends features defined in CSS 2, preserving backward compatibility. Work on CSS level 3 started around the time of publication of the original CSS 2 recommendation. The earliest CSS 3 drafts were published in June 1999

Summary of main module-specifications

|Module	|Specification title	|Status|	Date|
|-|-|-|-|
|css3-background|	CSS Backgrounds and Borders Module Level 3 |	Candidate Rec.|	Dec 2020|
|css3-box|	CSS basic box model|	Candidate Rec.	|Dec 2020|
|css-cascade-3|	CSS Cascading and Inheritance Level 3 	|Recommendation	Feb 2021
|css3-color|	CSS Color Module Level 3	|Recommendation	|Jun 2018|
|css3-content|	CSS3 Generated and Replaced Content Module |	Working Draft 2|	Aug 2019|
|css-fonts-3|	CSS Fonts Module Level 3|	Recommendation	|Sep 2018|
|css3-gcpm|	CSS Generated Content for Paged Media Module|	Working Draft|	May 2014|
|css3-layout|	CSS Template Layout Module	|Note	|Mar 2015|
|css3-mediaqueries |	Media Queries	|Recommendation|	Jun 2012|
|mediaqueries-4 |	Media Queries Level 4|	Candidate Rec.	|Jul 2020|
|css3-multicol| 	Multi-column Layout Module Level 1	|Working Draft	|Feb 2021|
|css3-page|	CSS Paged Media Module Level 3	|Working Draft	|Oct 2018|
|selectors-3|	Selectors Level 3	|Recommendation	|Nov 2018|
|selectors-4|	Selectors Level 4	|Working Draft	|Nov 2018|
|css3-ui|	CSS Basic User Interface Module Level 3 (CSS3 UI)|	Recommendation	|Jun 2018|
