实现0/5像素边框
---------------------------

实现0.5像素边框
   :PROPERTIES:
   :CUSTOM_ID: 实现0.5像素边框
   :END:

- 最简单方案

  - ```css
  - 只兼容ios

- 更好一点的方案

  - ```css

- 完美方案

  - ```css


省略号css
---------------------------

\\

单行省略号

overflow: hidden;

text-overflow: ellipsis;

white-space: nowrap;

\\

\\

多行省略号

 display: -webkit-box;\\

-webkit-box-orient: vertical;

-webkit-line-clamp: 2;

overflow: hidden;

\\





移动端自适应样式
---------------------------

移动端自适应样式
   :PROPERTIES:
   :CUSTOM_ID: 移动端自适应样式
   :END:

- 媒体查询

  - 针对不同的屏幕宽度，采用不同的样式，维护成本高

- Flex弹性布局

  - 设置viewport的值为固定值
  - 高度写死
  - 宽度自适应
  - 元素单位为px

- viewport缩放+rem

  - 根据rem将页面放大dpr倍, 然后viewport设置为1/dpr.

- rem布局

  - viewport固定
  - 使用js动态设置document根元素的fontsize



CSS单位
---------------------------
* #+tags: 前端，CSS

CSS单位
:PROPERTIES:
:id: css单位
   :CUSTOM_ID: css单位
:END:

- 绝对长度单位

  - cm
  - mm
  - in
  - px
  - pt
  - pc

- 相对长度单位

  - em
  - ex
  - ch
  - rem
  - vw
  - vh
  - vmin
  - vmax
  - %



CSS函数
---------------------------

CSS函数
   :PROPERTIES:
   :CUSTOM_ID: css函数
   :END:

- [[CSS2]]

  - attr

    - 返回选择元素的属性值。
    - attr(attribute-name)

      - attribute-name 必须。HTML 元素的属性名。

    - 例子

      - content: attr(href)

  - rgb

    - 使用红(R)、绿(G)、蓝(B)三个颜色的叠加来生成各式各样的颜色。
    - rgb(red, green, blue)

- [[CSS3]]

  - 颜色

    - rgba

      - 使用红(R)、绿(G)、蓝(B)、透明度(A)的叠加来生成各式各样的颜色。

    - hsl

      - 使用色相、饱和度、亮度来定义颜色。

    - hsla

      - 使用色相、饱和度、亮度、透明度来定义颜色。

  - 图像

    - cubic-bezier

      - 定义了一个贝塞尔曲线(Cubic Bezier)。

    - linear-gradient

      - 创建一个线性渐变的图像

    - radial-gradient

      - 用径向渐变创建图像。

    - repeating-linear-gradient

      - 用重复的线性渐变创建图像。

    - repeating-radial-gradient

      - 类似 radial-gradient()，用重复的径向渐变创建图像。

  - 属性

    - calc

      - 允许计算 CSS 的属性值，比如动态计算长度值。

    - var

      - 用于插入自定义的属性值。
      - var(custom-property-name, value)

        - custom-property-name 必需。自定义属性的名称，必需以 -- 开头。
        - value 可选。备用值，在属性不存在的时候使用。

      - 例子

        - ```css


css实现水平垂直居中
---------------------------

css实现水平垂直居中
   :PROPERTIES:
   :CUSTOM_ID: css实现水平垂直居中
   :END:

- 水平居中
- 垂直居中

  - [[flex]]方案

    - 设置父元素 ```css

  - [[CSS2]]方案

    - 核心点

      - 居中元素设置
      - ```css

  - [[CSS2]]Hack方案

    - ```css


BEM规范
---------------------------

BEM规范
   :PROPERTIES:
   :CUSTOM_ID: bem规范
   :END:

- 形式如class="block element modifier"
- block

  - 相当于一个明明空间

- element

  - bolck__xxx
  - 单独无意义，需要和block一起使用

- modifier

  - block-xx-xx
  - 和block或element一起使用

- 特点

  - 复用化
  - 单元化

