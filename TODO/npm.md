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
  Set a config with `--key val`.  All keys take a value, even if they are booleans (the config parser doesn't know what the options are at the time of parsing.)  If no value is provided, then the option is set to boolean `true`.

* 环境变量：
  Set any config by prefixing the name in an environment variable with `npm_config_`.  For example, `export npm_config_key=val`.

* 用户配置：
  The file at $HOME/.npmrc is an ini-formatted list of configs. If present, it is parsed.  If the `userconfig` option is set in the cli or env, then that will be used instead.

* 全局配置：
  The file found at ../etc/npmrc (from the node executable, by default this resolves to /usr/local/etc/npmrc) will be parsed if it is found.
  If the `globalconfig` option is set in the cli, env, or user config, then that file is parsed instead.

* 默认：
  npm's default configuration options are defined in lib/utils/config-defs.js.  These must not be changed.

更多信息参见 [`npm-config(7)`](https://docs.npmjs.com/misc/config)。

## CONTRIBUTIONS 贡献

欢迎贡献！

* 代码：
  Read through `npm-coding-style(7)` if you plan to submit code. You don't have to agree with it, but you do have to follow it.

* 文档：
  If you find an error in the documentation, edit the appropriate markdown file in the "doc" folder.  (Don't worry about generating the man page.)

贡献者列在 npm 的 `package.json` 文件中，可以通过 `npm view npm contributors` 来查看。

如果你想贡献，但不知道要做什么，请阅读贡献指南和检查问题列表。

* <https://github.com/npm/npm/wiki/Contributing-Guidelines>
* <https://github.com/npm/npm/issues>

## BUGS

When you find issues, please report them:

* web:
  <https://github.com/npm/npm/issues>

Be sure to include *all* of the output from the npm command that didn't work as expected.  The `npm-debug.log` file is also helpful to provide.

You can also look for isaacs in #node.js on irc://irc.freenode.net.  He will no doubt tell you to put the output in a gist or email.

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
