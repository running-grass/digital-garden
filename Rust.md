
## 宏
> 一种实现 [[元编程]] 的手段

### 优点
1. 可变参数
   由于Rust中的函数是固定参数的，所以宏的可变参数可以弥补这一点
2. 宏展开
### 缺点
1. 难于阅读和维护
2. 

## 声明式宏
最简单也最常见的宏。例如println!,panic!等
### 声明
```rust
#[macro_export] 
macro_rules! vec { 
	( $( $x:expr ),* ) => { 
		{ 
			let mut temp_vec = Vec::new(); 
			$( temp_vec.push($x); )* 
			temp_vec 
		} 
	}; 
}
```

### 使用
```rust
vec![1, 2, 3];
```

### 解释
1. 类似于一个可以展开的match语句块。
2. `$( $x:expr ),*` 为类似正则的宏模式
3. `=>` 后面的语句块为匹配成功后的展开代码
4. `#[macro_export]` 为导出声明式宏
## derive过程式宏
详见 [自定义 derive 过程宏](https://course.rs/advance/macro.html#%E8%87%AA%E5%AE%9A%E4%B9%89-derive-%E8%BF%87%E7%A8%8B%E5%AE%8F)
### 声明
```rust
#[proc_macro_derive(HelloMacro)] 
pub fn hello_macro_derive(input: TokenStream) -> TokenStream { 
	// 基于 input 构建 AST 语法树 
	let ast = syn::parse(input).unwrap(); 
	
	// 构建特征实现代码 
	impl_hello_macro(&ast) 
}


#![allow(unused)]
fn impl_hello_macro(ast: &syn::DeriveInput) -> TokenStream {
    let name = &ast.ident;
    let gen = quote! {
        impl HelloMacro for #name {
            fn hello_macro() {
                println!("Hello, Macro! My name is {}!", stringify!(#name));
            }
        }
    };
    gen.into()
}

```

### 使用
```rust
#[derive(HelloMacro)] 
struct Sunfei; 

#[derive(HelloMacro)] 
struct Sunface;
```
### 解释
1. 目前只能在单独的包中定义过程宏
2. 宏所在的包名自然也有要求，必须以 `derive` 为后缀，对于 `hello_macro` 宏而言，包名就应该是 `hello_macro_derive`
3. derive 宏输出的代码并不会替换之前的代码，而是追加
## 类属性宏(Attribute-like macros)

### 声明
```rust
#[proc_macro_attribute] 
pub fn route(attr: TokenStream, item: TokenStream) -> TokenStream {
}
```

### 使用
```rust
#[route(GET, "/")] 
fn index() {
}
```

### 解释
1. 宏定义有两个参数，第一个为使用时的宏参数，Get和"/"，第二个参数为宏标注的项（index函数）
2. 单独创建一个包，类型是 `proc-macro`，接着实现一个函数用于生成想要的代码。

## 类函数宏(Function-like macros)
### 声明
```rust
#[proc_macro] 
pub fn sql(input: TokenStream) -> TokenStream {
}
```
### 使用
```rust
let sql = sql!(SELECT * FROM posts WHERE id=1);
```
### 解释
1. 其与声明式宏比较像，区别在于声明式宏更简单一些，它只能进行模式匹配，而过程宏可以对输入串进行解析校验等操作。

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