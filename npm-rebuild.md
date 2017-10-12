npm-rebuild(1) -- 重新构建包
===================================
基于 [npm-rebuild(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-rebuild.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm rebuild [[<@scope>/<name>]...]

alias: npm rb
```
## DESCRIPTION 描述

该命令在匹配的文件夹上运行 `npm build` 命令。当你安装新版本的 node 时，这很有用，并且必须使用新的二进制文件重新编译所有 C++ 插件。

## SEE ALSO 亦可参阅

* [npm-build(1)](https://docs.npmjs.com/cli/build)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
