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
