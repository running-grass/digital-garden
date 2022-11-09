# package.json
## 字段说明
- main 模块中使用的入口文件
- types ts使用的导入字段，相当于main
- unpkg unpkg的缺省入口文件，相当于main
- jsnext:main es模块的入口
- module es模块入口
- jsdelivr jsdelivr的入口


# 相关工具
- npm-run-all 串行或者并行的运行多个npm脚本
- nrm 切换npm镜像，并可以检测各个镜像源的速度，在国内非常实用。
- pnpm 解决npm包版本冲突，node_modules.黑洞的解决方案


# npm更换镜像源

## 使用 `nrm`

1. 安装 nrm， npm i -g nrm
2. nrm test， 测试各个镜像的速度
3. nrm use aliyun , 选择一个延迟低的


# 添加git仓库

```bash
npm install git+ssh://git@github.com:npm/cli.git#v1.0.27
npm install git+ssh://git@github.com:npm/cli#semver:^5.0  
npm install git+https://isaacs@github.com/npm/cli.git
npm install git://github.com/npm/cli.git#v1.0.27
```
