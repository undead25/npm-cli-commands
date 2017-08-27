npm-init(1) -- 交互式创建一个 package.json 文件
=======================================================
基于 [npm-init(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-init.md) 官方文档翻译版本

## SYNOPSIS
```bash
npm init [-f|--force|-y|--yes]
```

## DESCRIPTION 描述

这会问你一些问题，然后为你生成一个 package.json。

它尝试对你想要设置的内容进行合理猜测，然后根据你选择的选项写入到一个 package.json 文件。

如果你已经有一个 package.json 文件了，那么它将首先读取这个文件，使用它里面的配置作为默认选项。

它是严格附加的，所以如果没有很好的理由，它不会删除你的 package.json 中已配置好的选项。

如果你使用 `-f`、`--force`、`-y` 或 `--yes` 选项来调用它，它将只使用默认值，而不会提示你任何选项。

## CONFIGURATION 配置

### scope 作用域

* 默认：无
* 类型：`String`

将被创建的包的作用域。

## SEE ALSO 亦可参阅

* <https://github.com/isaacs/init-package-json>
* [package.json(5)](https://docs.npmjs.com/files/package.json)
* [npm-version(1)](https://docs.npmjs.com/cli/version)
* [npm-scope(7)](https://docs.npmjs.com/misc/scope)
