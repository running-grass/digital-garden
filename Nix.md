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
- 