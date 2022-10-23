# macos下更换镜像源
## 更换channel
```bash
nix-channel --add https://mirrors.ustc.edu.cn/nix-channels/nixpkgs-unstable nixpkgs
nix-channel --update
```

## 更换二进制缓存
编辑 `/etc/nix/nix.conf`,然后添加
```ini
substituters = https://mirrors.ustc.edu.cn/nix-channels/store https://cache.nixos.org/
```


# Nixos 安装使用
## 下载镜像
https://nixos.org/download.html#nixos-iso
## 拷贝到USB
https://nixos.org/manual/nixos/stable/index.html#sec-booting-from-usb

#  文章
- [保姆级教你轻松掌握NixOS](https://www.lanta.cyou/2022/05/06/nixos-guide-cn/) 中文的安装教程
- [关于 Nix/NixOS 的核心概念介绍](https://zhuanlan.zhihu.com/p/523517998)
- [NIX FLAKES, Part 1: An introduction and tutorial](https://www.tweag.io/blog/2020-05-25-flakes) 介绍了为什么flakes 有帮助
- [灯花小屋](https://milena-blog.vercel.app/categories/NixOS/) 多篇nixos相关的博文
- [Anillc 的博客](https://anillc.cn/) 
- [Lan Tian 博客](https://lantian.pub/)

# 移动/nix目录到非系统盘
## 参考资料
https://nixos.wiki/wiki/Storage_optimization

## 增加分区
1. 使用 partd /dev/sdx 来进入交互模式，增加一个分区用于nix 目录
2. 使用 e2label 增加label

## 备份目录

## 设置自动挂载

## 删除旧的目录

# 安装使用clash
- 在nixos上面使用 `nix-env -iA nixos.clash`  安装软件
- 在macos上找到配置文件夹，把配置 config.yaml 上传到nixos上面
- 在nixos上建立文件夹，/etc/clash/ 
- 把config.yaml 放入到 /etc/clash 中。
- 重启服务
- 如果需要 使用 局域网ip 来代理，需要把config.yaml 中的allow-lan设置为true
