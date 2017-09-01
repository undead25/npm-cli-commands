npm-prune(1) -- 移除无关的包
==========================================
基于 [npm-prune(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-prune.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm prune [[<@scope>/]<pkg>...] [--production]
```

## DESCRIPTION 描述

此命令移除“无关”的包。如果提供了包名，那么只有名称匹配的那个包才会被移除。

无关的包指的是没有在父包的依赖关系列表中列出的包。

如果指定了 `--production` 标志，或者将 `NODE_ENV` 环境变量设置为 `production`，这个命令将移除 `devDependencies` 指定的包。设置 `--production=false` 将会否定 `NODE_ENV` 为 `production` 的设置。

## SEE ALSO 亦可参阅

* [npm-uninstall(1)](https://docs.npmjs.com/cli/uninstall)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-ls(1)](https://docs.npmjs.com/cli/ls)
