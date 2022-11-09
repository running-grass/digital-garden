是继承并扩展了部分[[ECMAScript]]规范的语言。各个浏览器在不同程度上实现了运行时。

# 运行时

- 各个浏览器
- nodejs
- deno
- [bun](https://bun.sh/) 高性能的运行时，基于webkit和jscore

# 相关工具
- npm-run-all 串行或者并行的运行多个npm脚本
- nrm 切换npm镜像，并可以检测各个镜像源的速度，在国内非常实用。
- pnpm 解决npm包版本冲突，node_modules.黑洞的解决方案
- 

# js中阻止事件的方法

- preventDefault 阻止事件的浏览器默认行为
- return false  阻止冒泡+默认行为
- stopImmediatePropagation 阻止事件冒泡，且不执行其它事件处理函数
- stopPropagation 阻止事件的冒泡，但是不阻止默认行为


# js中的模块化方案

- [[Web前端]]
- 由于历史原因，同时存在很多种非官方的模块化方案

  - [[AMD]]  是[[RequireJS]]推行的规范，异步加载，浏览器优先
  - [[CommonJS]]  nodejs端使用较多，同步加载文件
  - [[CMD]]   是[[SeaJS]]推行的规范，延迟加载
  - [[UMD]]  是[[AMD]]和[[CommonJS]]的综合体




实现数组去重

- 使用sort排序后，reduce判断，使用push
- 双层for循环
- 使用indexof判重
- 使用includes判重
- 使用对象键值对
- 使用Map数据类型
- 使用Set数据类型


# js更改光标位置

- 光标位置的获取

  - ```js
  - selectionStart获取选取的左边界，selectionEnd获取选区的右边界，当左右边界一致的时候，说明等于光标所在位置

- 设置光标


  - 本来这个是选中元素中的指定文本的，但是当start和end相同的时候，就会把光标移动至此，相应的还有



# apply bind call的区别

- fun.apply(thisArg,[argsArray])
- fun.bind(thisArg,arg1,arg2...)
- fun.call(thisArg,arg1,arg2,...)
- 共同点是都会把this绑定到第一个参数上
- apply和call都是直接执行函数返回结果的，bind是返回新函数
- apply的区别是，参数是通过数组传递

bind和其它的区别是，返回绑定this后的新函数，它允许提供部分参数，下次调用只需要提供剩余的参数，


作用域链

作用域链
   :PROPERTIES:
   :CUSTOM_ID: 作用域链
   :END:

- 全局作用域内会包含局部作用域
- 局部作用域会相互嵌套
- 应用

  - 当执行函数或使用变量时
  - 会先从最内层的局部作用域查找
  - 如果找不到，会查找上一层级的局部作用域
  - 直到全局作用域，如果还没有找到，

- 只能单向向上查找访问，不能向下查找


new操作符的执行过程
- [[Web前端]][[js]]

  1. 创建一个空对象

- 

  2. 链接到construct的原型对象

- 

  3. 绑定this指向

- 

  4. 执行构造函数

- 

  5. 返回新对象或者指定的返回值（非基本数据类型）


# npm更换镜像源

## 使用 `nrm`

1. 安装 nrm， npm i -g nrm
2. nrm test， 测试各个镜像的速度
3. nrm use aliyun , 选择一个延迟低的


# Promise

- 异步编程的一种解决方案，比回调函数和事件机制要优雅一些
- 本质上是一个容器，封装了一个异步事件。
- 基本用法

  - ```js

- 分为三种状态

  - pending
  - resolved
  - rejected

- 有5个方法

  - Promise.prototype.then(resolvedFn, rejectedFn)

    - 第一个函数是resolved之后的回调，携带data
    - 第二个是rejected之后的回调，会携带error

  - Promise.prototype.catch(rejectedFn)

    - 等效于Promise.prototype.then(null, rejectedFn)

  - Promise.prototype.finally()

    - 无论rejected还是resolved都会触发的回调

  - )
  - Promise.all(iterable)

    - ```js
    - 所有的promise全部resolved才会整体resolved。
    - 如果有一个是rejected，那么整体就会是rejected

  - Promise.race(iterable)

    - 只要有一个resolved/rejected，就会整体resolved/rejected

- 特点

  - 对象的状态不受外部的影响，只能由内部的异步操作来转换状态
  - 一旦从pending状态转变为rejected/resolved之后，就不会再发生改变了

- 缺点

  - 一旦新建立刻执行，无法取消
  - 如果不设置rejected回调的话，内部的error无法传递到外部
  - 在pending状态时，无法查看具体的执行状态


# Iterator和stream的区别

- iterator的作用的用来遍历，单向遍历
- 而stream的区别是提供了相关计算操作的高级iterator


# 链式调用

链式调用
   :PROPERTIES:
   :CUSTOM_ID: 链式调用
   :END:

- 可以参考的类库有2个

  - [[Stream]]
  - [[Immutable]]
  - [[Rxjs]]
  - [[Lodash]]



# stream和transducers的关系


Transducers会把用到的函数组合进行复用，而stream只是在利用小函数进行链式调用
- Transducers和Stream都可以完成类似的功能和效果 *
对数组只遍历一遍 
- Stream没有办法对一段逻辑过程进行复用。




# JavaScript与有限状态机

- [[有限状态机]]是一个有用的模型
- 对应的是面向对象设计模式汇总的state模式
- 包含三个特征

  - 状态总数是有限的
  - 任一时刻，只处于一种状态之下
  - 某种条件下会从一种状态转变为另外一种状态

- 例如

  - 网页上的菜单元素

    - 当鼠标悬停的时候现实菜单
    - 当鼠标移开的时候隐藏菜单
    - 如果使用状态机来表示

      - 元素一共有两种状态

        - 显示
        - 隐藏

      - 鼠标的悬停会改变元素的状态

  - 红绿灯也可以视为一个状态机

    - 一共有三种状态

      - 红灯
      - 绿灯
      - 黄灯

    - 根据信号，有四种事件可以改变状态

      - 警告 从绿灯变黄灯
      - 停止 从黄灯变红灯
      - 准备 从红灯变黄灯
      - go 从黄灯变绿灯

- 相关[[js类库]]

  - https://github.com/jakesgordon/javascript-state-machine][javascript-state-machine








# 原型链的原理
- 原型主要是为了解决对象的属性共享问题

每个对象都会有一个原型对象，访问一个对象的某一属性的时候，会先在自身的props中查找，如果找不到，会去查找其原型对象的props

而由于原型对象也是对象，所以原型对象也会有它的原型对象。如此递归查找，知道某一个对象的原型对象为null

找不到该属性，就会报错 * 相关 * __propto__指向原型对象 *
[[new操作符的执行过程]]
