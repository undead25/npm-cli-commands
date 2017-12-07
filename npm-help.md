npm-help(1) -- 获得关于 npm 的帮助
==============================
基于 [npm-help(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-help.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm help <term> [<terms..>]
```

## DESCRIPTION 描述

如果提供了主题，则会显示适当的文档页面。

如果没有主题，或者提供了多个术语，则运行 `help-search` 命令查找匹配项。请注意，如果 `help-search` 只找到一个主题，那么它将在该主题上运行 `help`，因此唯一匹配等同于指定主题名称。

## CONFIGURATION 配置

### viewer 展示器

* 默认：Posix： "man"，Windows："browser"
* 类型：`path`

用于查看帮助内容的程序。

设置为 `"browser"` 以便在默认的 Web 浏览器中查看 html 帮助内容。

## SEE ALSO 亦可参阅

* [npm(1)](https://docs.npmjs.com/cli/npm)
* [README](https://github.com/npm/npm/blob/latest/README.md)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
* [npm-help-search(1)](https://docs.npmjs.com/cli/help-search)
* [npm-index(7)](https://docs.npmjs.com/misc/index)
