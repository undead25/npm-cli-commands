# npm install-test(1) -- 安装包并运行测试
基于 [npm-install-test(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-install-test.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm install-test (with no args, in package dir)
npm install-test [<@scope>/]<name>
npm install-test [<@scope>/]<name>@<tag>
npm install-test [<@scope>/]<name>@<version>
npm install-test [<@scope>/]<name>@<version range>
npm install-test <tarball file>
npm install-test <tarball url>
npm install-test <folder>

alias: npm it
common options: [--save|--save-dev|--save-optional] [--save-exact] [--dry-run]
```

## DESCRIPTION 描述

这个命令首先运行 `npm install`，紧接着运行 `npm test`。它与 `npm install` 的参数完全相同。

## SEE ALSO 亦可参阅

- [npm-install(1)](https://docs.npmjs.com/cli/install)
- [npm-test(1)](https://docs.npmjs.com/cli/test)
