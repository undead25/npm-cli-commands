npm-prefix(1) -- 显示（目录）前缀
===============================
基于 [npm-prefix(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-prefix.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm prefix [-g]
```

## DESCRIPTION 描述

打印本地目录前缀。如果没有 `-g`，它是 package.json 文件最近的父目录。

如果带有 `-g`，它将是全局目录前缀。更多细节可参考 [`npm-config(7)`](https://docs.npmjs.com/misc/config)。

## SEE ALSO 亦可参阅

* [npm-root(1)](https://docs.npmjs.com/cli/root)
* [npm-bin(1)](https://docs.npmjs.com/cli/bin)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
