npm-cache(1) -- 操作包缓存
==========================================
基于 [npm-cache(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-cache.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm cache add <tarball file>
npm cache add <folder>
npm cache add <tarball url>
npm cache add <name>@<version>

npm cache clean [<path>]
aliases: npm cache clear, npm cache rm

npm cache verify
```


## DESCRIPTION 描述

用于添加，列出或清理 npm 缓存文件夹。

* `add`：
  将指定的包添加到本地缓存。此命令主要用于在 npm 内部使用，但它可以提供一种将数据显式添加到本地安装缓存的方法。

* `clean`：
  从缓存文件夹中删除所有数据。

* `verify`：
  验证缓存文件夹的内容，垃圾回收任何不需要的数据，以及验证缓存索引和所有缓存数据的完整性。


## DETAILS 详情

npm 将缓存数据存储在通过 `cache` 配置的不透明目录中，名为 `_cacache`。该目录是基于 `cacache` 的缓存内容可寻址的，用于存储所有的 http 请求数据以及其他与包相关的数据。该目录主要通过`pacote` 访问，该库负责从 npm@5 获取的所有包。

通过缓存的所有数据已全部验证了插入和提取的完整性。缓存损坏将触发错误，或者向 `pacote` 发出数据必须重新获取信号，它将自动执行。因此，除了回收磁盘空间以外，没有清除缓存的必要，这就是为什么 `clean` 现在需要 `--force` 来运行。

目前没有通过 npm 暴露的方法来检查或直接管理此缓存的内容。为了访问它，必须直接使用 `cacache`。

npm 不会自动删除数据：缓存将随着安装新的包而增长。

## A NOTE ABOUT THE CACHE'S DESIGN 关于缓存设计的说明

npm 缓存严格来说是一个缓存：它不应该依赖于持久可靠的数据存储来存放包数据。npm 不保证先前缓存的数据将在以后可用，并且将自动删除损坏的内容。缓存主要是保证，如果它返回数据，那么这些数据就是插入的数据。

要对现有缓存内容进行离线验证，请使用 `npm cache verify`。

## CONFIGURATION 配置

### cache 缓存位置

默认：可移植性操作系统：`~/.npm`，Windows：`%AppData%/npm-cache`。

根缓存文件夹。

## SEE ALSO 亦可参阅

* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-pack(1)](https://docs.npmjs.com/cli/pack)
* [https://npm.im/cacache](https://npm.im/cacache)
* [https://npm.im/pacote](https://npm.im/pacote)
