npm-outdated(1) -- 检查过时的包
==============================================
基于 [npm-outdated(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-outdated.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm outdated [[<@scope>/]<pkg> ...]
```


## DESCRIPTION 描述
此命令将检查注册表来查看是否有（或指定）已安装的包目前已过时。

这将输出：

* `wanted` 是满足 `package.json` 指定的语义化版本范围的包的最大版本。如果没有可用的语义化版本范围（即运行 `npm outdated --global`，或者包没有包含在 `package.json` 中），那么 `wanted` 显示当前安装的版本。
* `latest` 是注册表中被标记为最新版本的包。如果 `npm publish` 没有特殊的配置将发布包含 `latest` 的 dist-tag。这可能是也可能不是包的最大版本，或最近发布的包版本，具体取决于包的开发人员如何管理最新的 [`dist-tag(1)`](https://docs.npmjs.com/cli/dist-tag)。
* `location` 是包在依赖关系树中的哪个位置。请注意，`npm outdated` 的深度缺省值为 0，因此除非重写，否则将始终只会看到顶级依赖关系过时。
* `package type`（当使用 `--long` / `-l` 时）会告诉你这个包是 `dependency` 还是 `devDependency`。package.json 中未包含的包始终被标记为 `dependencies`。


### An example 示例

```bash
$ npm outdated
Package      Current   Wanted   Latest  Location
glob          5.0.15   5.0.15    6.0.1  test-outdated-output
nothingness    0.0.3      git      git  test-outdated-output
npm            3.5.1    3.5.2    3.5.1  test-outdated-output
local-dev      0.0.3   linked   linked  test-outdated-output
once           1.3.2    1.3.3    1.3.3  test-outdated-output
```

有这样的 `dependencies`：
```json
{
  "glob": "^5.0.15",
  "nothingness": "github:othiym23/nothingness#master",
  "npm": "^3.5.1",
  "once": "^1.3.1"
}
```

需要注意的是：

* `glob` 需要 `^5`，这样可以防止 npm 安装 在语义化版本之外的 `glob@6`。
* Git 依赖关系将永远会被重新安装，因为它们是这样被指定的。已安装的 committish 可能会满足依赖关系说明符（如果它是不可变的，就像提交的 SHA），或者它可能不会，所以 `npm outdated` 和 `npm update` 必须获取 Git 参考来进行检查。这就是为什么当前正在重新安装的 Git 依赖关系总是导致新的克隆和安装。
* `npm@3.5.2` 被标记为 `wanted`，但 `latest` 是 `npm@3.5.1` ，因为 npm 使用 dist-tag 来管理其 `latest` 和 `next` 的发布通道。`npm update` 将安装 **newest** 版本，但是 `npm install npm`（没有语义化版本范围）会安装任何被标记为 `latest` 的包。
* `once` 只是普通的过时。从头开始重装 `node_modules` 或运行 `npm update` 将会使其达到预期。

## CONFIGURATION 配置

### json

* 默认：`false`
* 类型：`Boolean`

以 JSON 格式展示信息。

### long

* 默认：`false`
* 类型：`Boolean`

展示额外的信息。

### parseable

* 默认：`false`
* 类型：`Boolean`

显示可分析的输出，而不是树状图图。

### global

* 默认：`false`
* 类型：`Boolean`

检查全局安装的包，而不是在当前项目中的。

### depth

* 默认：`0`
* 类型：`Int`

检查依赖关系树的最大深度。

## SEE ALSO 亦可参阅
* [npm-update(1)](https://docs.npmjs.com/cli/update)
* [npm-dist-tag(1)](https://docs.npmjs.com/cli/dist-tag)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
