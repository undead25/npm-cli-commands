npm-link(1) -- 为包文件夹创建软连接
=======================================
基于 [npm-link(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-link.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm link (in package dir)
npm link [<@scope>/]<pkg>[@<version>]

alias: npm ln
```


## DESCRIPTION 描述
包链接有两个步骤。

首先，在包文件夹中执行 `npm link` 命令，这将在全局包文件夹 `{prefix}/lib/node_modules/<package>` 中创建一个软连接。（参见 [`npm-config（7）`](https://docs.npmjs.com/misc/config) 中的 `prefix` 值）。这还会将包中的任何 bin 都链接到 `{prefix}/bin/{name}`。

接下来，在某个其他位置，`npm link package-name` 命令会将全局安装的 `package-name` 链接到当前文件夹的 `node_modules/` 中。


注意:`package-name` 来源于 `package.json` 而不是目录名称。

包名称可以带作用域前缀。参见 [`npm-scope（7）`](https://docs.npmjs.com/misc/scope)。作用域之前必须有 `@/`。

当为 `npm publish` 创建压缩包时，通过解析软链接，将链接的包“快照”到其当前的状态。

这对于安装自己的东西非常方便，可以对其进行处理和重复测试，而无需不断重复构建。

例如：
```bash
cd ~/projects/node-redis    # go into the package directory
npm link                    # creates global link
cd ~/projects/node-bloggy   # go into some other package directory.
npm link redis              # link-install the package
```

现在，`~/projects/node-redis` 的任何更改都将反映在 `~/projects/node-bloggy/node_modules/node-redis/` 中。请注意，链接的是包名称，而不是该包的目录名称。

你也可以将这两个步骤合并成一个。例如，上述用例也可以这样：
```bash
cd ~/projects/node-bloggy  # go into the dir of your main project
npm link ../node-redis     # link the dir of your dependency
```

第二行相当于：
```bash
(cd ../node-redis; npm link)
npm link node-redis
```

也就是说，它首先创建一个全局的链接，然后将全局安装目标链接到项目的 `node_modules` 文件夹中。

如果链接的包是有作用域的（参见[`npm-scope（7）`](https://docs.npmjs.com/misc/scope)），那链接命令也必须包含该作用域，例如
```bash
npm link @myorg/privatepackage
```


## SEE ALSO 亦可参阅
* [npm-developers(7)](https://docs.npmjs.com/misc/developers)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
