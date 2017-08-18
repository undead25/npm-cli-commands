npm-config(1) -- 管理 npm 配置文件
===================================================
基于 [npm-config(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-config.md) 官方文档翻译版本


## SYNOPSIS 概要
```bash
npm config set <key> <value> [-g|--global]
npm config get <key>
npm config delete <key>
npm config list [-l]
npm config edit
npm get <key>
npm set <key> <value> [-g|--global]

aliases: c
```


## DESCRIPTION 描述

npm 从命令行、环境变量、`npmrc` 文件以及某些情况下 `package.json` 文件中获取其配置设置。

有关 npmrc 文件的更多信息，请参阅 [npmrc(5)](https://docs.npmjs.com/files/npmrc)。

关于所涉及机制的深入讨论，请参阅 [`npm-config(7)`](https://docs.npmjs.com/misc/config)。

`npm config` 命令可用于更新和编辑用户以及全局 npmrc 文件里面内容。

## Sub-commands 子命令

配置支持以下子命令：

### set 设置
```bash
npm config set key value
```
将配置键设置为该值。

如果省略值，则表示将其设置为 `true`。

### get 获取
```bash
npm config get key
```
将配置值回显到 `stdout`。

### list 列出
```bash
npm config list
```
显示所有配置设置。 使用 `-l` （译者注：`npm config list -l`）也可以显示默认值。

### delete 删除
```bash
npm config delete key
```

从所有配置文件中删除键。

### edit 编辑
```bash
npm config edit
```

在编辑器中打开配置文件。 使用 `--global` 标志来编辑全局配置。

## SEE ALSO 亦可参阅
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm(1)](https://docs.npmjs.com/cli/npm)
