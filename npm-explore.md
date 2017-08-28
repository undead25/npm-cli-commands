npm-explore(1) -- 浏览已安装的包
=============================================
基于 [npm-explore(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-explore.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm explore <pkg> [ -- <command>]
```


## DESCRIPTION 描述

在指定的安装包的目录中生成一个 subshell。

如果指定了一个命令，那么它将在 subshell 中运行，然后立即终止。

在 `node_modules` 文件夹中有 git 子模块的情况下，这是特别方便的：

```bash
npm explore some-dependency -- git pull origin master
```

请注意，该包是**不**自动构建的，所以如果你进行了任何更改，请一定要使用 `npm rebuild <pkg>`。

## CONFIGURATION 配置

### shell

* 默认：SHELL 环境变量，Posix：`bash`，Windows：`cmd`
* 类型：`path`

运行 `npm explore` 命令的 shell。

## SEE ALSO 亦可参阅

* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-edit(1)](https://docs.npmjs.com/cli/edit)
* [npm-rebuild(1)](https://docs.npmjs.com/cli/rebuild)
* [npm-build(1)](https://docs.npmjs.com/cli/build)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
