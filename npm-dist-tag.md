npm-dist-tag(1) -- 修改包的发布标签
===================================================
基于 [npm-dist-tag(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-dist-tag.md) 官方文档翻译版本

## SYNOPSIS 概述
```bash
npm dist-tag add <pkg>@<version> [<tag>]
npm dist-tag rm <pkg> <tag>
npm dist-tag ls [<pkg>]

aliases: dist-tags
```


## DESCRIPTION 描述

添加、删除和列出包的发布标签：

* `add`：
  给包的指定版本打上指定的标签，如果未指定标签，则使用 `--tag` 的配置。

* `rm`：
  清除包不再使用的标签

* `ls`：
  显示包所有的发布标签，默认为当前目录前缀的包。

在安装包的时候，标签可以作为包版本的引用来使用，而不必使用指定的版本号：

```bash
npm install <name>@<tag>
```

当安装依赖时，可以指定首选标签版本：

```bash
npm install --tag <tag>
```

这同样适用于 `npm dedupe`.

除非使用了 `--tag` 选项，发布包将给已发布的版本打上 `latest` 标签。例如，`npm publish --tag=beta`。

默认情况下，`npm install <pkg>`（没有指定 `@<version>` 或 `@<tag>`）将安装 `latest` 标签的版本。

## PURPOSE 目的

标签可用于提供别名而不是版本号。

例如，一个项目可能选择拥有多个开发流，并为每个流使用不同的标签，像 `stable`、`beta`、`dev`、`canary`。

默认情况下，npm 使用 `latest` 标签来标识包的当前版本，`npm install <pkg>`（没有指定 `@<version>` 或 `@<tag>`）将安装 `latest` 标签的版本。通常情况下，项目只能使用 `latest` 标签来发布稳定的版本，不稳定的版本则使用其他标签，如预发布版本。

一些项目使用 `next` 标签来标识即将发布的版本。

默认情况下，除 `latest` 以外，没有其他标签对于 npm 本身具有特殊的意义。

## CAVEATS 警告

这个命令以前是 `npm tag`，它只创建了新的标签，所以有一个不同的语法。

标签必须与版本号共享一个名称空间，因为它们是在一条语句中：`npm install <pkg>@<version>` vs `npm install <pkg>@<tag>`。

可以被解释为有效的语义化版本范围的标签会被拒绝。例如，`v1.4` 不能用作标签，因为它被解释为 `>=1.4.0 <1.5.0`。请参阅<https://github.com/npm/npm/issues/6082>。

避免标签发生语义化版本问题的最简单的方法是，使用不以数字或字母 `v` 开头的标签。

## SEE ALSO 亦可参阅

* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-dedupe(1)](https://docs.npmjs.com/cli/dedupe)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
