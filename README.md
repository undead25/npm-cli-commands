npm(1) -- 一个 JavaScript 包管理器
==============================

[![Build Status](https://img.shields.io/travis/npm/npm/latest.svg)](https://travis-ci.org/npm/npm)

> - 在线阅读：<https://undead25.gitbooks.io/npm-cli/content/>
> - 对比更新：[Link](https://github.com/npm/npm/compare/latest...undead25:latest>)（这个方法比较蠢，欢迎你提供比较好的方法 🙂 ）


## 概要

本篇只是提供启动和运行 npm 的基本信息。

一旦完成安装，你可以通过 `npm help` 来获取更多的信息。

## IMPORTANT 重要

**你需要 v4 或者更高版本的 node 来运行 npm**

要在 node v0.12 以及之前版本上安装的旧的**和不再支持的** npm 版本，请克隆 git 仓库，然后通过旧的标签和分支找到对应的版本。

**npm 默认配置为使用 npm 公司的公共包注册表 <https://registry.npmjs.org>。**

你可以通过配置来使用任何你喜欢的兼容的注册表，甚至运行你自己的注册表。请查看[注册表文档](https://docs.npmjs.com/misc/registry)。

使用他人的注册表可能受使用条款的约束。默认公共注册表的使用条款请参见  <https://www.npmjs.com>。

## 超级简易安装

npm 已与 [node]((https://nodejs.org/en/download/)) 捆绑在一起进行安装。

### Windows

[获取 MSI](https://nodejs.org/en/download/)。里面包含了 npm。

### Mac

[获取 pkg](https://nodejs.org/en/download/)。里面包含了 npm。

### 其他

运行 `make install`。npm 将于 node 一起被安装。

如果你想要一个更自由安装方式（不同的版本，自定义路径等），请继续阅读。

## Fancy Install (Unix)

There's a pretty robust install script at <https://www.npmjs.com/install.sh>.  You can download that and run it.

下面是一个使用 curl 的例子：

```sh
curl -L https://www.npmjs.com/install.sh | sh
```

### Slightly Fancier

你可以使用这个脚本设置任何 npm 配置参数：

```sh
npm_config_prefix=/some/path sh install.sh
```

Or, you can run it in uber-debuggery mode:

```sh
npm_debug=1 sh install.sh
```

### Even Fancier

Get the code with git.  Use `make` to build the docs and do other stuff. If you plan on hacking on npm, `make link` is your friend.

If you've got the npm source code, you can also semi-permanently set arbitrary config keys using the `./configure --key=val ...`, and then run npm commands by doing `node bin/npm-cli.js <command> <args>`.  (This is helpful for testing, or running stuff without actually installing npm itself.)

## Windows 安装和升级

Many improvements for Windows users have been made in npm 3 - you will have a better experience if you run a recent version of npm. To upgrade, either use [Microsoft's upgrade tool](https://github.com/felixrieseberg/npm-windows-upgrade), [download a new version of Node](https://nodejs.org/en/download/), or follow the Windows upgrade instructions in the [npm Troubleshooting Guide](./TROUBLESHOOTING.md).

If that's not fancy enough for you, then you can fetch the code with git, and mess with it directly.

## 在 Cygwin 安装

不支持。

## 卸载

很遗憾你会这么做。

```sh
sudo npm uninstall npm -g
```
如果失败了，你可以这样：

```sh
sudo make uninstall
```

## More Severe Uninstalling

Usually, the above instructions are sufficient.  That will remove npm, but leave behind anything you've installed.

If you would like to remove all the packages that you have installed, then you can use the `npm ls` command to find them, and then `npm rm` to remove them.

To remove cruft left behind by npm 0.x, you can use the included `clean-old.sh` script file.  You can run it conveniently like this:

```sh
npm explore npm -g -- sh scripts/clean-old.sh
```

npm uses two configuration files, one for per-user configs, and another
for global (every-user) configs.  You can view them by doing:

```sh
npm config get userconfig   # defaults to ~/.npmrc
npm config get globalconfig # defaults to /usr/local/etc/npmrc
```

Uninstalling npm does not remove configuration files by default.  You must remove them yourself manually if you want them gone.  Note that this means that future npm installs will not remember the settings that you have chosen.

## More Docs 更多文档

查看 [文档](https://docs.npmjs.com/).

你可以使用 `npm help` 命令来了解它们中的任何一个。

如果你是一个开发者，并且想用 npm 来发布程序，那你应该[阅读这个](https://docs.npmjs.com/misc/developers)。

## BUGS

当你发现问题时，请上报给我们：

* 网站：<https://github.com/npm/npm/issues>

确保包含 npm 命令不能按预期工作所输出的**所有**内容。提供 `npm-debug.log` 文件也是有帮助的。

You can also find npm people in `#npm` on https://package.community/ or [on Twitter](https://twitter.com/npm_support).  Whoever responds will no doubt tell you to put the output in a gist or email.

## SEE ALSO 亦可参阅
* [npm(1)](https://docs.npmjs.com/cli/npm)
* [npm-help(1)](https://docs.npmjs.com/cli/help)
* [npm-index(7)](https://docs.npmjs.com/misc/index)

---
## 译者述

为方便阅读，本文提供 .pdf、.epub、或 .mobi 格式的电子书下载：

<https://www.gitbook.com/book/undead25/npm-cli/details>

---

![](https://i.creativecommons.org/l/by-nc/4.0/88x31.png)

本文档基于 [知识共享署名-非商业性使用 4.0 国际许可协议](http://creativecommons.org/licenses/by-nc/4.0/) 发布。
