npm(1) -- JavaScript 包管理器
====================================

## SYNOPSIS 概要
```bash
npm <command> [args]
```

## VERSION 版本

@VERSION@

## DESCRIPTION 描述

npm 是 Node JavaScript 平台的包管理器。它将模块放在合适的地方以便 node 找到，并智能地管理依赖冲突。

灵活的配置使它支持各种用例，通常用于发布，发现，安装和开发 node 程序。

运行 `npm help` 来获得可用命令的列表。

## INTRODUCTION 介绍

你可能因为想安装东西才使用了 npm。

使用 `npm install blerg` 来安装最新版本的 `blerg`。查看 [`npm-install(1)`](https://docs.npmjs.com/cli/install) 来了解更多信息，它可以做很多事情。

使用 `npm search` 命令来显示所有可用的包。使用`npm ls` 来显示所有已经安装的包。

## DEPENDENCIES 依赖关系

如果一个包引用另一个包含 git URL 的包，那么 npm 依赖已预先安装的 git。

如果 npm 试图安装的包中有一个是本地的 node 模块，并且需要编译 C++ 代码，那么 npm 将使用 [node-gyp](https://github.com/TooTallNate/node-gyp) 来执行该任务。

在 Unix 系统上，[node-gyp](https://github.com/TooTallNate/node-gyp) 需要 Python，make 以及像 GCC 的构建链。在 Windows 上，需要 Python 和 Microsoft Visual Studio C++。Python 3 不支持 [node-gyp](https://github.com/TooTallNate/node-gyp)。更多相关信息，请访问 [node-gyp 仓库](https://github.com/TooTallNate/node-gyp) 和 [node-gyp Wiki](https://github.com/TooTallNate/node-gyp/wiki)。

## DIRECTORIES 目录

参阅 [`npm-folders(5)`](https://docs.npmjs.com/files/folders) 来了解 npm 将内容放在哪里。

特别的是 npm 有两种操作模式：

* 全局模式： 
  npm 将包安装在 `prefix/lib/node_modules` 中，而 bin 则安装在 `prefix/bin` 中。

* 本地模式：
  npm 将包安装到当前工程的目录中，该目录默认为当前工作目录。包被安装到 `./node_modules` 中，bin 被安装到  `./node_modules/.bin`。

默认为本地模式。可以在任意命令上使用 `-g` 或者 `--global` 让其在全局模式下运行。 

## DEVELOPER USAGE 开发者说明

如果你使用 npm 来开发和发布代码，请查看以下帮助主题：

* `json`：
  创建一个 `package.json` 文件。参见 [`package.json(5)`](https://docs.npmjs.com/files/package.json)。

* `link`：
  使用 `npm link` 来将当前工作代码链接到 Node 的路径中，以便每次更改时不必重新安装。

* `install`：
  如果你不需要软连接，那么安装是个好主意。特别是从注册表安装其他人的代码，通过 `npm install` 来完成。

* `adduser`：
  创建帐户或登录。凭证存储在用户配置文件中。

* `publish`：
  使用 `npm publish` 命令来上传你的代码到注册表中。

## CONFIGURATION 配置

npm 具有灵活的配置，从 5 个地方读取其配置选项。

* 命令行开关：
  用 `--key val` 设置一个配置。所有的键都有一个值，即使它们是布尔值（配置解析器不知道解析时的选项是什么）。如果没有提供值，那么该选项会被设置为布尔值 `true`。

* 环境变量：
  通过 `npm_config_` 在环境变量中加上前缀来设置配置。例如 `export npm_config_key=val`。

* 用户配置：
  $HOME/.npmrc 中的文件是一个 ini 格式的配置列表。如果存在，则进行解析。如果在 cli 或 env 中设置了 `userconfig` 选项，那么将会使用它。

* 全局配置：
  在 ../etc/npmrc 找到的文件（从 node 可执行文件中，默认情况下会被解析为 /usr/local/etc/npmrc）将被解析。如果在 cli、env 或者 user config 中设置了 `globalconfig` 选项，那么就会解析这个文件。

* 默认：
  npm 的默认配置选项是在 lib/utils/config-defs.js 中定义的。这些配置不能被改变。

更多信息参见 [`npm-config(7)`](https://docs.npmjs.com/misc/config)。

## CONTRIBUTIONS 贡献

欢迎贡献！

* 代码：
  如果你打算提交代码，请阅读 [`npm-coding-style(7)`](https://docs.npmjs.com/misc/coding-style)。你不必同意，但你必须遵循它。

* 文档：
  如果在文档中发现错误，请在 `doc` 文件夹中编辑相应的 markdown 文件。（不要担心会生成手册页。）

贡献者列在 npm 的 `package.json` 文件中，可以通过 `npm view npm contributors` 来查看。

如果你想贡献，但不知道要做什么，请阅读贡献指南和检查问题列表。

* <https://github.com/npm/npm/wiki/Contributing-Guidelines>
* <https://github.com/npm/npm/issues>

## BUGS

当你发现问题，请报告给我们：

* web：<https://github.com/npm/npm/issues>

确保包含 npm 命令不能按预期工作所输出的**所有**内容。提供 `npm-debug.log` 文件也是有帮助的。

你也可以在 irc://irc.freenode.net 上的 #node.js 中找到 isaacs。他毫无疑问会告诉你把输出结果放在 gist 上或者电子邮件中。

## AUTHOR 作者
[Isaac Z. Schlueter](http://blog.izs.me/) ::
[isaacs](https://github.com/isaacs/) ::
[@izs](http://twitter.com/izs) ::
<i@izs.me>

## SEE ALSO 亦可参阅
* [npm-help(1)](https://docs.npmjs.com/cli/help)
* README
* [package.json(5)](https://docs.npmjs.com/files/package.json)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-index(7)](https://docs.npmjs.com/)
