npm-bugs(1) -- 包在 web 浏览器中可能出现的错误
========================================================


## SYNOPSIS 概要
```bash
npm bugs [<pkgname>]

aliases: issues
```


## DESCRIPTION 描述
该命令尝试猜测包的错误跟踪 URL 的可能位置，然后尝试使用 `--browser` 配置参数打开它。如果没有提供包名称，它将在当前文件夹中搜索 `package.json` 并使用 `name` 属性。

## CONFIGURATION 配置

### browser 浏览器
* 默认：OS X：`"open"`、Windows：`"start"`、其它：`"xdg-open"`
* 类型： `String`

`npm bugs` 命令调用浏览器打开网站。

### registry 注册表

* 默认：`https://registry.npmjs.org/`
* 类型：`url`

npm 包注册表的基本 URL。


## SEE ALSO 亦可参阅

* [npm-docs(1)](https://docs.npmjs.com/cli/docs)
* [npm-view(1)](https://docs.npmjs.com/cli/view)
* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
