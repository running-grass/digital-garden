Promise
---------------------------

Promise
   :PROPERTIES:
   :CUSTOM_ID: promise
   :END:

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
