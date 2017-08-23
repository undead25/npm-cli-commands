npm-docs(1) -- 在 web 浏览器中的包文档（也许）
========================================================
基于 [npm-docs(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-docs.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm docs [<pkgname> [<pkgname> ...]]
npm docs .
npm home [<pkgname> [<pkgname> ...]]
npm home .
```


## DESCRIPTION 描述

此命令尝试猜测包文档 URL 的可能位置，然后尝试使用 `--browser` 配置参数打开它。你可以一次传递多个包名称。如果没有提供包名称，它将在当前文件夹中搜索一个 `package.json` 并使用 `name` 属性值。

## CONFIGURATION 配置

### browser 浏览器

* 默认：OS X：`"open"`，Windows：`"start"`，Others：`"xdg-open"`
* 类型：`String`

`npm docs` 命令调用浏览器打开网站。

### registry 注册表

* 默认：[https://registry.npmjs.org/](https://registry.npmjs.org/)
* 类型：`url`

npm 包注册表的基本 URL。


## SEE ALSO 亦可参阅

* [npm-view(1)](https://docs.npmjs.com/cli/view)
* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
