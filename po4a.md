# 配置项目
## 增加配置文件
```cfg po4a.cfg
[options] --master-charset UTF-8
[options] --localized-charset UTF-8
[options] --addendum-charset UTF-8
[options] --master-language en

[po4a_langs] zh_Hans
[po4a_paths] pot/$master.pot $lang:po/$lang/$master.po

[type: text] ../README.md $lang:./README.md opt:"-k 1"
```
其中 `type: $type` 写多个


# 相关链接
- [po4a cli 手册](https://man.archlinux.org/man/po4a.1p.zh_CHS)
