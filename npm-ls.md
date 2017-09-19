npm-ls(1) -- 列出已安装的包
======================================
基于 [npm-ls(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-ls.md) 官方文档翻译版本


## SYNOPSIS 概要
```bash
npm ls [[<@scope>/]<pkg> ...]

aliases: list, la, ll
```


## DESCRIPTION 描述
此命令将以树状结构打印所有已安装包的版本和它们之间的依赖关系。

位置参数 `name@version-range` 会将结果限制为指定包的路径。需要注意的是，嵌套包**也会**显示指定包的路径。例如，在 npm 源码树中运行 `npm ls promzard` 将显示：

```bash
npm@@VERSION@ /path/to/npm
└─┬ init-package-json@0.0.4
    └── promzard@0.1.5
```
这将打印出无关的，缺失的和无效的包。

如果一个项目为依赖关系指定了 git url，那么它们将在 name@version 之后的括号中显示，以便用户更容易地识别项目的潜在分支。

显示的树是逻辑依赖关系树，基于包依赖关系，而不是 node_modules 文件夹的物理布局。

当以 `ll` 或 `la` 运行时，默认情况下会显示扩展信息。

## CONFIGURATION 配置

### `json`

* 默认：`false`
* 类型：`Boolean`

以``JSON` 格式显示信息。

### `long`

* 默认：`false`
* 类型：`Boolean`

显示扩展信息。

### `parseable`

* 默认：`false`
* 类型：`Boolean`

显示可分析输出，而不是树状图。

### `global`

* 默认：`false`
* 类型：`Boolean`

列出全局安装的包，而不是当前项目中安装的包。

### depth

* 类型：`Int`

依赖关系树的最大显示深度。

### `prod` / `production`

* 类型：`Boolean`
* 默认：`false`

仅显示 `dependencies` 中的包的依赖关系树。

### `dev`

* 类型：`Boolean`
* 默认：`false`

仅显示 `devDependencies` 中的包的依赖关系树。

### `only`

* 类型：`String`

当值为 `dev` 或 `development` 时，是 `dev` 的别名。

当值为 `prod` 或 `production` 时，是 `production` 的别名。

### `link`

* 类型：`Boolean`
* 默认：`false`

仅显示被链接的包的依赖关系


## SEE ALSO 亦可参阅
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-link(1)](https://docs.npmjs.com/cli/link)
* [npm-prune(1)](https://docs.npmjs.com/cli/prune)
* [npm-outdated(1)](https://docs.npmjs.com/cli/outdated)
* [npm-update(1)](https://docs.npmjs.com/cli/update)
