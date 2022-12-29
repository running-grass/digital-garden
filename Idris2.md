Idris是一个纯函数式的通用编程语言
也可以简单的看作是[[Haskell]]的改良版

可编译为[[JavaScript]]和[[Nodejs]]

实现了[[定量类型系统]]

## 安装使用
1. mac可以使用homebrew 来安装idris 2
2. 可以通过pack工具来安装
3. 通过 [源码安装](https://github.com/idris-lang/Idris2/blob/main/INSTALL.md)


## 自 Idris 1增加的内容
1.  [[定量类型系统]]的支持
2. 


## 函数
### 命名参数
类型声明中可以为参数命名，命名后可以使用按名称传参数调用，包括记录语法

`fromMaybe { deflt = False }`

或者对于记录
`MkDragon { strength = 150, name = "Gorgar", hitPoints = 10000 }`



## 工具链
- https://github.com/stefan-hoeck/idris2-pack 软件安装工具

## 类库
- https://github.com/kbertalan/tyttp http服务端，提供了一个nodejs的客户端
- https://github.com/octeep/idris2-http 一个idris2的客户端
- https://github.com/Russoul/Idris2-Effect

## 相关链接
- https://github.com/stefan-hoeck/idris2-tutorial 英文教程
- https://github.com/xgrommx/idris-ecosystem 生态
- https://www.manning.com/books/type-driven-development-with-idris TDD在线阅读
- https://github.com/idris-lang/Idris2/wiki/1-%5BLanguage%5D-Libraries  idris2 相关类库链接
- https://github.com/stefan-hoeck/idris2-pack-db/blob/main/STATUS.md pack可用的包
- https://github.com/joaomilho/awesome-idris awesome 列表
- https://github.com/idris-hackers/idris-koans idris 教程
- https://idris-zh.rtfd.io/ 中文idris1教程，进度60%左右，已弃坑
- [Agda vs. Coq vs. Idris](https://whatisrt.github.io/dependent-types/2020/02/18/agda-vs-coq-vs-idris.html)  几个类haskell语言的对比
- [Idris2 Documentation Browser](https://idris2docs.sinyax.net/) 便于搜索Idris2 的文档
- [quickdocs](https://idris2-quickdocs.surge.sh/) 更全的一个关于Idris2 的文档，基于pack-db进行聚合
- [Rhone Js](https://github.com/stefan-hoeck/idris2-rhone-js)  单页面MVC框架，类比 [[Vue]] 和 [[PureScript]] 中的 Halogen，但是其不使用VDom，而是直接操作真实dom

## 杂项
1. 调用命令行命令  System.run 

### 使用基于NonEmpty List的head函数
```haskell

test: List Nat -> Nat
test ns = case ns of
  [] => 0
  xs@(_::_) => head xs
```


不像[[PureScript]]那样，在 idris2 中 record 不能继承，但是应该可以通过 元编程和依赖类型来模拟。继承和鸭子类型
