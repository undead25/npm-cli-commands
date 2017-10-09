npm-unpublish(1) -- 从注册表中移除包
======================================================

## SYNOPSIS 概要
```bash
npm unpublish [<@scope>/]<pkg>[@<version>]
```

## WARNING 警告

**删除其他人有依赖的版本库通常被认为是不良行为！**

如果你的目的是鼓励用户进行升级，请考虑使用 `deprecate` 命令。

注册表上有充足空间。

## DESCRIPTION 描述

从注册表中移除包版本，并删除其入口和压缩包。

如果没有指定版本，或者所有版本都被删除，则完全从注册表中删除包的入口。

即使取消发布包版本，也不能重复使用指定的名称和版本组合。为了再次发布包，必须使用新的版本号。

使用默认注册表（`registry.npmjs.org`），只有在过去 24 小时内发布的版本才允许取消发布。 如果你尝试取消发布之前的版本，请联系 [support@npmjs.com](mailto:support@npmjs.com)。

作用域是可选的，遵循 [`npm-scope（7）`](https://docs.npmjs.com/misc/scope) 的常规规则。

## SEE ALSO 亦可参阅
* [npm-deprecate(1)](https://docs.npmjs.com/cli/deprecate)
* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-adduser(1)](https://docs.npmjs.com/cli/adduser)
* [npm-owner(1)](https://docs.npmjs.com/cli/owner)
