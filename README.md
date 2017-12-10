npm(1) -- 一个 JavaScript 包管理器
==============================

[![Build Status](https://img.shields.io/travis/npm/npm/latest.svg)](https://travis-ci.org/npm/npm)

> - 在线阅读：<https://undead25.gitbooks.io/npm-cli/content/>
> - 对比更新：[Link](https://github.com/npm/npm/compare/latest...undead25:latest)（这个方法比较蠢，欢迎你提供比较好的方法 🙂 ）


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

npm 已与 [node]((https://nodejs.org/en/download/)) 捆绑在一起进行安装。

### Windows

[获取 MSI](https://nodejs.org/en/download/)。里面包含了 npm。

### Mac

[获取 pkg](https://nodejs.org/en/download/)。里面包含了 npm。

### 其他

运行 `make install`。npm 将于 node 一起被安装。

如果你想要一个更自由安装方式（不同的版本，自定义路径等），请继续阅读。

## 自由安装（Unix）

在 <https://www.npmjs.com/install.sh> 上有一个非常强大的安装脚本。你可以下载并运行它。

下面是一个使用 curl 的例子：

```sh
curl -L https://www.npmjs.com/install.sh | sh
```

### 有点自由

你可以使用这个脚本设置任何 npm 配置参数：

```sh
npm_config_prefix=/some/path sh install.sh
```

或者，你可以在超级调试模式下运行它：

```sh
npm_debug=1 sh install.sh
```

### 更自由

通过 git 获取源码。使用 `make` 来构建文档和其它的事情。如果你打算在 npm 上进行二次开发，可以使用 `make link`。

如果你有 npm 源码，你也可以使用 `./configure --key=val ...` 半永久性地设置任意配置键，然后通过 `node bin/npm-cli.js <command> <args>` 来运行 npm 命令。（这有助于测试或运行，而不需要实际安装 npm 自身。）

## Windows 安装和升级
npm 3 对 Windows 用户进行了许多改进 - 如果运行最新版本的 npm，你将获得更好的体验。要升级，你可以使用 [Microsoft 的升级工具](https://github.com/felixrieseberg/npm-windows-upgrade)、[下载新版本的 Node](https://nodejs.org/en/download/) 或者按照 [npm 故障排除指南](./TROUBLESHOOTING.md)中的 Windows 升级说明进行操作。

如果这对你来说还不够自由，那么你可以用 git 来获取源码，并直接对其进行处理。

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

## More Severe Uninstalling 更彻底的卸载

通常情况下，上面的说明已经足够了。它们将删除 npm，但会保留所有你已经安装的包。

如果你想删除所有你已经安装的包，那么你可以使用 `npm ls` 命令找到它们，然后通过 `npm rm` 来删除它们。

要删除 npm 0.x 的残留，可以使用附带的 `clean-old.sh` 脚本文件。你可以像这样很方便地运行它：

```sh
npm explore npm -g -- sh scripts/clean-old.sh
```

npm 使用两个配置文件，一个是用户配置，另一个是全局配置。你可以这样查看它们：

```sh
npm config get userconfig   # 默认是 ~/.npmrc
npm config get globalconfig # 默认是 /usr/local/etc/npmrc
```

卸载 npm 默认不会删除配置文件，你必须手动删除它们。请注意，这意味着以后的 npm 安装将不会记住你已经选择了的设置。

## More Docs 更多文档

查看 [文档](https://docs.npmjs.com/).

你可以使用 `npm help` 命令来了解它们中的任何一个。

如果你是一个开发者，并且想用 npm 来发布程序，那你应该[阅读这个](https://docs.npmjs.com/misc/developers)。

## BUGS 错误

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
