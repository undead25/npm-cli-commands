npm-update(1) -- 包更新
=================================
基于 [npm-update(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-update.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm update [-g] [<pkg>...]

aliases: up, upgrade
```


## DESCRIPTION 描述

此命令将更新所有列出的包到最新版本（由 `tag` 配置指定），遵循语义化版本。

它还将安装缺少的包。与其他安装包的命令一样，`--dev` 标志也会导致 `devDependencies` 被处理。

如果指定 `-g` 标志，则此命令将更新全局安装的包。

如果没有指定包名称，那么指定位置（全局或本地）中的所有包将被更新。

从 `npm@2.6.1` 开始，`npm update` 只会检查顶层的包。以前的版本会递归检查所有的依赖项，要达到这种效果，请使用 `npm --depth 9999 update`。


## EXAMPLES 示例
重要版本提示：这些示例假定 `npm@2.6.1` 或更高版本。对于旧版本的 `npm`，必须指定 `--depth 0` 来达到下面描述的效果。

对于下面的示例，假设当前的包是 `app`，它依赖 `dep1`（`dep2`，……等等）。 `dep1` 已发布的版本如下：

```json
{
  "dist-tags": { "latest": "1.2.2" },
  "versions": [
    "1.2.2",
    "1.2.1",
    "1.2.0",
    "1.1.2",
    "1.1.1",
    "1.0.0",
    "0.4.1",
    "0.4.0",
    "0.2.0"
  ]
}
```

### 插入符依赖

如果 `app` 的 `package.json` 包括：

```json
"dependencies": {
  "dep1": "^1.1.1"
}
```

那 `npm update` 会安装 `dep1@1.2.2`，因为 `1.2.2` 是 `latest` 的，并且 `1.2.2` 满足 `^1.1.1`

### 波浪号依赖

然而，如果 `app` 的 `package.json` 包括：

```json
"dependencies": {
  "dep1": "~1.1.1"
}
```

在这种情况下，运行 `npm update` 会安装 `dep1@1.1.2`。即使 `latest` 标签指向了 `1.2.2`，但该版本不满足 `~1.1.1`（`>=1.1.1 <1.2.0`），所以使用了满足`~1.1.1` 的最高排序的 `1.1.2` 版本 。

### 低于 1.0.0 版本的插入符依赖

假设 `app` 有一个低于 `1.0.0` 版本的插入符依赖，例如：

```json
"dependencies": {
  "dep1": "^0.2.0"
}
```

`npm update` 会安装 `dep1@0.2.0`，因为没有满足 `^0.2.0` 的其他版本。

如果依赖的版本是 `^0.4.0`：

```json
"dependencies": {
  "dep1": "^0.4.0"
}
```

那 `npm update` 将会安装 `dep1@0.4.1`，因为它是满足 `^0.4.0`（`>= 0.4.0 <0.5.0`）的最高排序版本。

### 通过 `--save` 记录更新

当你需要更新包并且将新版本作为最低依赖保存在 `package.json` 中时，可以使用 `npm update -S` 或 `npm update --save`。例如，如果 `package.json` 包括：

```json
"dependencies": {
  "dep1": "^1.1.1"
}
```

那 `npm update --save` 将会安装 `dep1@1.2.2`（即 `latest`），并且 `package.json` 会被修改成：

```json
"dependencies": {
  "dep1": "^1.2.2"
}
```

请注意，如果安装新包，`npm` 只会将更新了的版本写入 `package.json`。

### 更新全局安装的包

`npm update -g` 会将 `update` 操作应用到已安装的每个 `outdated` 全局包，也就是说，与 `latest` 不同的版本。

注意：如果包升级到了比 `latest` 还新的包，那么它将被**降级**。

## SEE ALSO 亦可参阅
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-outdated(1)](https://docs.npmjs.com/cli/outdated)
* [npm-shrinkwrap(1)](https://docs.npmjs.com/cli/shrinkwrap)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-ls(1)](https://docs.npmjs.com/cli/ls)
