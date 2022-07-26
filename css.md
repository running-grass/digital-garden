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
