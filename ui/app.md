[TOC]

# App

## App是什么

app是什么意思？app在手机中的意思就是application的简称，也就是应用的意思，通常用于iphone手机，也可以是安卓等其他手机应用。app是什么？app是英文Application的简称，由于iPhone智能手机的流行，现在的app多指智能手机的第三方应用程序。目前比较著名的App商店有Apple的iTunes商店里面的App Store，android的Google Play Store，诺基亚的ovi store，还有Blackberry用户的，BlackBerry App World。那么app是什么？

app是什么意思的问题总结，简单的理解就是，app就是应用软件，现在主要指的都是ios、mac、android等系统下的应用软件。

## App的分类

### 按开发方式分类

- Native App
- Web App
- Hybrid App

### 按内容分类

- 游戏
- 购物

## IOS的设计规范

### 设计稿尺寸规范

| 手机           | 对角线 | 逻辑像素    |物理像素    | LPPI | 设备像素比 |
| -------------- | ------ | ----------- |----------- | ---- | ---------- |
| iPhone 5       | 4.0    | 640×1136    |320 × 568    | 326  | 2          |
| iPhone 5s      | 4.0    | 640×1136    | 320 × 568 |326  | 2          |
| iPhone SE      | 4.0    | 640×1136    | 320 × 568 |326  | 2          |
| iPhone 6       | 4.7    | 750 x 1334  | 375 × 667 |326  | 2          |
| iPhone 6s      | 4.7    | 750 x 1334  | 375 × 667 |326  | 2          |
| iPhone 7       | 4.7    | 750 x 1334  | 375 × 667 |326  | 2          |
| iPhone 8       | 4.7    | 750 x 1334  | 375 × 667 |326  | 2          |
| iPhone 6 Plus  | 5.5    | 1242 x 2208* | 414 × 736 |401  | 3          |
| iPhone 6s Plus | 5.5    | 1242 x 2208* | 414 × 736 |401  | 3          |
| iPhone 7 Plus  | 5.5    | 1242 x 2208* | 414 × 736 |401  | 3          |
| iPhone 8 Plus  | 5.5    | 1242 x 2208* | 414 × 736 |401  | 3          |
| iPhone X       | 5.8    | 1125 x 2436 | 375 × 812 |458  | 3          |
| iPhone XR      | 6.1    | 828 x 1792  | 414 × 896 |326  | 2          |
| iPhone XS      | 5.8    | 1125 x 2436 |375 × 812    | 458  | 3          |
| iPhone XS MAX  | 6.5    | 1242 x 2688 | 414 × 896 |458  | 3          |

注：官网标注1080×1920分辨率为渲染分辨率，实际截图的分辨率是1242×2208。

- 设计稿尺寸：750*1334（基准尺寸)
  + 兼容性好：向上(415pt)和向下(320pt)调整幅度最小

### 界面元素

- status bar (状态栏):
  + 位于整个App最顶部
  + 可改变背景色使其与APP整体风格统一
  + 用于显示信号、日期、电量等元素。
  + Height: 40px

- Navigation bar (导航栏)
  + 位于状态栏下方
  + 起导航作用，一般会显示标题
  + 也可放控件，如搜索框、分段式控件
  + 底色一般为app主色调
  + Height: 88px

- Search bar (搜索栏)

  + 位于导航栏上或下
  + 用于搜索控件
  + height: 88px

- Scope bar (范围栏)

  + 位于搜索栏下，一般和搜索栏同时出现
  + 用于定义用户搜索的范围
  + Height: 60-88px

- Tab bar (标签栏)
  + 位于app最底部
  + 用于放常用图表 一般最多不超过5个 超过5个使用更多展示
  + Height: 98px

- Tool bar (工具栏)
  + 位于app最底部
  + 用于放操作当前界面的一些控件
  + Height: 88px

- List (常规列表)
  + 位于内容视图中
  + 用于展示内容
    * 文本内容
    * 图片内容
  * 图文内容
  + 列表之间常使用1像素线分割
  
- List (卡片列表)
  + 位于内容视图中
  + 用于将内容归纳到矩形卡片中
  + 卡片可以覆盖、移动
  + 可增加描边、阴影，使其具有立体感
  
- Collection (集合视图)
  + 位于内容视图中
  + 用于将同类信息以平铺的形式展示
  + 一般以图片为主、文字为辅
  + 常见于电商、图片或音乐等App
  
- Collection (内容视图)
  + 位于内容视图中
  + 图片视图：纯图片 常见于图片、社交类app
  + 文本视图：纯文本  常见于内容类app
  
### 字体规范

- 中文字体：苹方
- 英文字体：sanfrancisco

### 字号规范

- 舒适值
  + 长文本：32px - 34px
  + 短文本：32px
  + 注释：28px
- 见小值：50%用户认为小
  + 长文本：30px
  + 短文本：30px
  + 注释：24px
- 可接受下限：80%用户可接受
  - 长文本：26px
  - 短文本：26px
  - 注释：24px
- 顶部导航
  + 中间字号：一般为36px 或 42px
  + 两侧字号：36px
- 底部导航
  + 常用22px
  + 可接受：20-24px
- 文章中
  + 大标题：36px
  + 正文：28px 30px
  + 小标题：24px
- 新闻类标题切换
  + 常规30px
  + 当前40px

### 图标尺寸规范

44px

48px

50px

### 间距尺寸规范

常用间距：20px 或 30px

 ## 安卓设计规范

### 设计稿尺寸

- 720 × 1280
- 1080× 1920 （720× 1280× 1.5）

### 栏高度

- 状态栏：50px
- 导航栏：96px
- 标签栏：96px

### 字号大小

最好是4的倍数

- 24px
- 28px
- 32px
- 36px

### 图标尺寸

最好是4的倍数

- 启动图标尺寸
  + 48px
  + 72px
  + 96px
  + 36px

### 字体

- 英文：roboto
- 中文：Noto或思源黑体 (最新)
- 中文：方正兰亭黑 / 细黑体(4.0以上主流用法)

### 元素间距

最好是4的倍数

- 16px

  

  

  










## Reference

- [https://thinkmobiles.com/blog/popular-types-of-apps/](https://thinkmobiles.com/blog/popular-types-of-apps/)
- [https://blog.trigent.com/different-types-of-mobile-applications-native-hybrid-and-web-apps](https://blog.trigent.com/different-types-of-mobile-applications-native-hybrid-and-web-apps)
- 

