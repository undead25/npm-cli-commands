npm-uninstall(1) -- 删除包
=============================
基于 [npm-uninstall(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-uninstall.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm uninstall [<@scope>/]<pkg>[@<version>]... [-S|--save|-D|--save-dev|-O|--save-optional|--no-save]

aliases: remove, rm, r, un, unlink
```

## DESCRIPTION 描述

卸载一个包，完全删除 npm 安装的所有东西。

示例：
```bash
npm uninstall sax
```

在全局模式下（即在命令后加上 `-g` 或 `--global`），它会将当前包的上下文作为全局包卸载。

`npm uninstall` 有 3 个可选标志，用于保存或更新 package.json 中的包版本：

* `-S, --save`：包将从 `dependencies` 中删除.

* `-D, --save-dev`：包将从 `devDependencies` 中删除.

* `-O, --save-optional`：包将从 `optionalDependencies` 中删除.

* `--no-save`：包将不会从 `package.json` 文件中删除.

另外，如果有 `npm-shrinkwrap.json·，那么它也会被更新。

作用域是可选的，并且遵循 [`npm-scope(7)`](https://docs.npmjs.com/misc/scope) 的基本规则。

示例：
```bash
npm uninstall sax --save
npm uninstall @myorg/privatepackage --save
npm uninstall node-tap --save-dev
npm uninstall dtrace-provider --save-optional
npm uninstall lodash --no-save
```

## SEE ALSO 亦可参阅
* [npm-prune(1)](https://docs.npmjs.com/cli/prune)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
