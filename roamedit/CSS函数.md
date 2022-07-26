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
