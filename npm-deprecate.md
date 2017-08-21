npm-deprecate(1) -- 废弃包的某个版本
====================================================
基于 [npm-deprecate(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-deprecate.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm deprecate <pkg>[@<version>] <message>
```


## DESCRIPTION 描述

此命令将更新包的 npm 注册表入口，为尝试安装它的所有人提供一个废弃警告。

它适用于版本范围以及特定版本，因此你可以执行以下操作：
```bash
npm deprecate my-thing@"< 0.2.3" "critical bug fixed in v0.2.3"
```

请注意，你必须是包的所有者才能废弃某些内容。请参阅 `owner` 和 `adduser` 帮助主题。

要取消废弃包，可以为 `message` 参数指定一个空字符串（`""`）。

## SEE ALSO 亦可参阅

* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
