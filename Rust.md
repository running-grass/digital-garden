
## 宏
> 一种实现 [[元编程]] 的手段

### 优点
1. 可变参数
   由于Rust中的函数是固定参数的，所以宏的可变参数可以弥补这一点
2. 宏展开
### 缺点
1. 难于阅读和维护
2. 
## 定义方式
### 使用方式
```
println!("{}, {}!", "hello", "world");
```

## 生态
### web开发领域
### 前端框架
- [Dioxus](https://dioxuslabs.com/)  react风格的前端UI库，使用 render 语法
- [cargo-web](https://crates.io/crates/cargo-web) — A Cargo subcommand for the client-side We
- [sauron](https://github.com/ivanceras/sauron) - Client side web framework which closely adheres to The Elm Architecture. 
- [seed](https://seed-rs.org/) — A Rust framework for creating web apps
- [stdweb](https://crates.io/crates/stdweb) — A standard library for the client-side Web
- [yew](https://crates.io/crates/yew) — Rust framework for making client web apps
#### 后端框架
axum
actix-web
warp
poem
rocket
### 异步运行时
tokio
async-std
smol

Tauri RUST生态下的GUI开发工具，类似 Electron

## 相关链接
[Rust 中文文档翻译](https://rustwiki.org/zh-CN/)
[Axum.教程](https://programatik29.github.io/axum-tutorial/#/)
[Rust 圣经](https://course.rs/) 
[rust学习资源列表](https://github.com/ctjhoa/rust-learning)
[Let's build a browser engine!](http://limpet.net/mbrubeck/2014/08/08/toy-layout-engine-1.html) 使用Rust构建一个浏览器引擎