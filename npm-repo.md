npm-repo(1) -- 在浏览器中打开包仓库页面
========================================================
基于 [npm-repo(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-repo.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm repo [<pkg>]
```

## DESCRIPTION 描述

此命令尝试猜测包仓库 URL 可能的位置，然后再使用 `--browser` 配置参数打开它。如果没有提供包名称，它将在当前文件夹中搜索`package.json` 文件，并使用其 `name` 属性的值。


## CONFIGURATION 配置

### browser 浏览器

* 默认：OS X：`"open"`，Windows：`"start"`，Others：`"xdg-open"`
* 类型：`String`

`npm repo` 命令调用的浏览器打开网站。

## SEE ALSO 亦可参阅

* [npm-docs(1)](https://docs.npmjs.com/cli/docs)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
