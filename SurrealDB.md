使用的查询语言类似于SQL，但是扩展了很多内容。

# 启动
## 启动内存版本
```bash
surreal start
```

## 启动单机硬盘持久化
```bash
surreal start -- file:/tmp/surrealdb
```

# 字段类型
用在 DEFINE 的语句中
- bool 布尔类型
- recotd(tableName) 记录引用类型，指向某一张表
- object 对象类型
- string 
- number 
- 
# 目前支持的客户端
- wasm
- js
- deno
- Rust
- python
