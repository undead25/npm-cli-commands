npm-pack(1) -- 为包创建一个压缩包
==============================================
基于 [npm-pack(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-pack.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm pack [[<@scope>/]<pkg>...]
```

## DESCRIPTION 描述

对于任何可安装的东西（即包文件夹、压缩包、压缩包路径、name@tag、name@version、名称或作用域名称），这个命令将把它缓存起来，然后将压缩包复制到当前工作目录，命名为 `<name>-<version>.tgz`，再将文件名写入 stdout。

如果多次声明相同的包，则文件将被第二次覆盖。

如果没有提供参数，那么 npm 打包当前的包文件夹。

## SEE ALSO 亦可参阅

* [npm-cache(1)](https://docs.npmjs.com/cli/cache)
* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
