apply bind call的区别
---------------------------

apply bind call的区别
   :PROPERTIES:
   :CUSTOM_ID: apply-bind-call的区别
   :END:

- fun.apply(thisArg,[argsArray])
- fun.bind(thisArg,arg1,arg2...)
- fun.call(thisArg,arg1,arg2,...)
- 共同点是都会把this绑定到第一个参数上
- apply和call都是直接执行函数返回结果的，bind是返回新函数
- apply的区别是，参数是通过数组传递

bind和其它的区别是，返回绑定this后的新函数，它允许提供部分参数，下次调用只需要提供剩余的参数，
