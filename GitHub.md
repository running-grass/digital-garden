## action

action 市场 https://github.com/marketplace?query=cache

### 常用的action

[Cache](https://github.com/marketplace/actions/cache)
[Checkout](https://github.com/actions/checkout)

### 手动触发
在对应的action文件中增加
```yml
on:
  workflow_dispatch: {}
```
### 小技巧
- 使用checkout可以检出子仓库
- 如果要操作github上的其它仓库，需要在checkout 中指定自定义的pat，然后在其他的step中可以使用push
- 在action中想使用commit，需要先配置 config user.username 和 user.email
- 

# 国内使用

## 翻墙代理

## 加速代理

https://doc.fastgit.org/
