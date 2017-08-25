npm-edit(1) -- 编辑已安装的包
========================================
基于 [npm-edit(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-edit.md) 官方文档翻译版本

## SYNOPSIS 概述
```bash
npm edit <pkg>[@<version>]
```


## DESCRIPTION 描述

用默认编辑器（或者你通过 npm `editor` 配置的其他编辑器 —— 请参阅 [`npm-config（7)`](https://docs.npmjs.com/misc/config)）打开包文件夹。

编辑完成后，包将重新被构建，以便接收编译包中的任何更改。

例如，你可以使用 `npm install connect` 将 `connect` 安装到你的包中，然后使用 `npm edit connect` 对本地安装的副本进行一些更改。

## CONFIGURATION 配置

### editor 编辑器

* 默认：如果设置了环境变量，`EDITOR` , 或者可移植操作系统上的 `"vi"`, 或者 Windows 上的 `"notepad"`.
* 类型：`path`

这个命令用于运行 `npm edit` 或者 `npm config edit`。

## SEE ALSO 亦可参阅

* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-explore(1)](https://docs.npmjs.com/cli/explore)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
