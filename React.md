## 状态管理
- Redux 曾经的经典的状态管理库，过于繁琐

### 各个流派
-   没有状态管理工具：直接用 props 或者 context
-   单项数据流：`redux`、`zustand`
-   双向绑定：`mobx`、`valtio`
-   状态原子化：`jotai`、`recoil`
-   有限状态机：`xstate`

### Jotai 与 Zustand 有何不同？
- Jotai 就像 Recoil。Zustand 就像 Redux。
- 为了保持状态，两者都有可以存在于模块级别或上下文级别的存储。Jotai 被设计为上下文第一，模块第二。Zustand 被设计为首先是模块，其次是上下文。
- Jotai 状态由原子组成（即自下而上）。Zustand 状态是一个对象（即自上而下）。
- 主要区别在于状态模型。Zustand 是一个单一的商店（尽管你可以创建多个单独的商店），而 Jotai 由原始原子组成并允许将它们组合在一起。从这个意义上讲，这是编程心智模型的问题。

-  什么时候用哪个
	-   如果你需要替换 useState+useContext，Jotai 很合适。
	-   如果你想要一个简单的模块状态，Zustand 非常适合。
	-   如果代码拆分很重要，那么 Jotai 应该表现不错。
	-   如果你更喜欢 Redux devtools，Zustand 是个不错的选择。
	-   如果你想使用 Suspense，Jotai 就是其中之一。