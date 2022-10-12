---
title: "把npm包同时发布到多个注册表"
date: 2022-06-28T09:11:51+08:00
tags:
  - npm
  - register
  - github
  - node
  - javascript
  - 解决方案
draft: false
---

本文介绍了如何把一个npm包同时发布到npm注册表和github的注册表，其它注册表同理。

<!--more-->

# 需求背景

我有一个基于lerna的项目，包含了多个package，我一开始是发布到github pkg register的。虽然发github可以在仓库直接关联上，但是对于使用者来说会很麻烦，所以我就像能不能同时发到npm和github上。

# 解决方案

通过`npm-multi-publish`来支持这个功能，好处是不光`npm publish`可以自动发布到多个注册表，任何基于`npm publish`的都可以。例如`lerna publish`

# 实施步骤

1. 在`~/.npmrc`中增加对多个注册表的认证。 如下所示
```
//registry.npmjs.org/:_authToken=npm_xxxxxxxxxxxxxxxxxx
//npm.pkg.github.com/:_authToken=ghp_yyyyyyyyyyyyyyyyyy
```

2. 验证是否登录成功，执行下列命令后会回显对应的用户名
```bash
npm whoami --registry=https://registry.npmjs.org/ 
npm whoami --registry=https://npm.pkg.github.com/
```

3. 在package.json总增加对应的配置

```json 
{
    "publishConfig": [ // 注册表列表，有多少个写多少个
    {
      "registry": "https://registry.npmjs.org"
    },
    {
      "registry": "https://npm.pkg.github.com"
    }
  ],
  "scripts": { // 增加两个npm发布的生命周期钩子
    "prepublishOnly": "npm-multi-publish", //  在npm publish命令前执行
    "postpublish": "npm-multi-publish", // 在npm publish命令后执行
  }
}

```

4. 执行`npm publish`或`lerna publish`

# 原理

1. 在执行`npm publish`后, 通过`prepublishOnly`拦截发布操作，提取`publishConfig`数组，然后使用第一个注册表项覆盖`publishConfig`配置，写入package.json文件，然后正常执行`publish`
2. 通过`postpublish`钩子，但第一个注册表发布完成后，把`publishConfig`改成第二个注册表现，并写入文件。然后执行额外的`npm publish`
3. 上一步的`npm publish`会继续触发`postpublish`和`prepublishOnly`
4. 当`postpublish`检测到所有的注册表都发布完之后，会复原`package.json`文件

# 注意事项
1. 如果是发不到npm的组织中的话，需要先单独的`npm publish --access public`,因为默认会作为组织的私有包，如果没有花钱的话，手动指定为公开的包

2. 如果已经在项目的.npmrc中指定该package的注册表，需要删除掉

# 相关链接