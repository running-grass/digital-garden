# 在mac上使用git而不安装xcode
1. 安装 Xcode 命令行工具 xcode-select --install
2. 确认安装成功 xcode-select --version
3. 切换xcode的路径 sudo xcode-select --switch /Library/Developer/CommandLineTools

# git子模块

- 添加
  - git submodule add
- 克隆项目后使用
  - git submodule init
  - git submodule update
- 提交宿主仓库中对子模块的修改
  - git add submodule
  - 需要手动add

# 小技巧

## 查看已删除文件的logged
```bash
git log --all --full-history -- <path-to-file>
```