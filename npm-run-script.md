npm-run-script(1) -- 运行任意包脚本
==================================================
基于 [npm-run-script(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-run-script.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm run-script <command> [--silent] [-- <args>...]

alias: npm run
```

## DESCRIPTION 描述

运行 `"scripts"` 对象中定义的任意命令。如果没有提供 `"command"`，将列出可用的脚本。`run[-script]` 被用于测试、启动、重新启动和停止命令，但也可以直接调用。当包中的脚本被打印出来时，它们被拆分为生命周期（测试、启动、重新启动）和直接运行的脚本。

从 [`npm@2.0.0`](http://blog.npmjs.org/post/98131109725/npm-2-0-0) 开始，执行脚本时可以使用自定义参数。[getopt](http://goo.gl/KxMmtG) 所使用的特殊选项 `--` 用来界定选项的结尾。npm 会把 `--` 后的所有参数直接传递给你的脚本：
```bash
npm run test -- --grep="pattern"
```

参数只会传递到 **`npm run`** 指定的脚本后面，而不会传递到 `pre` 或 `post` 脚本后面。

`env` 脚本是一个特殊的内置命令，它可以用于列出脚本在运行时可用的环境变量。如果在包中定义了一个 `env` 命令，它将优先于内置命令。

除了 `shell` 预先存在的 `PATH` 外，`npm run` 将 `node_modules/.bin` 添加到 `PATH` 中来提供给脚本。本地安装的依赖关系所提供的任何二进制文件，都可以在不使用 `node_modules/.bin` 前缀的情况下被使用。例如，如果你的包中有一个 `devDependency` 的 `tap`，你应该这样写：
```js
"scripts": {"test": "tap test/\*.js"}
```
而不是这样
```js
"scripts": {"test": "node_modules/.bin/tap test/\*.js"}  
```
来运行你的测试。

无论当前调用 `npm run` 的工作目录是什么，脚本都从模块的根目录运行。如果希望脚本根据所在的子目录使用不同的行为，可以使用 `INIT_CWD` 环境变量，它在你运行 `npm run` 时保持你所在的完整路径。

`npm run` 将 `NODE` 环境变量设置为 `npm` 执行的 `node` 可执行文件。另外，如果传递了 `--scripts-prepend-node-path`，那么`node` 所在的目录会被添加到 `PATH` 中。 如果传递了 `--scripts-prepend-node-path=auto`（这在 `npm` v3 中是默认的），那只有在 `PATH` 中找不到 `node` 可执行文件时才执行此操作。

在没有 `node_modules` 目录下运行脚本会失败，并将被给予一个运行 `npm install` 的警告来以防你忘记了。

可以使用 `--silent` 标志来阻止出现 `npm ERR!` 错误输出。

## SEE ALSO 亦可参阅
* [npm-scripts(7)](https://docs.npmjs.com/misc/scripts)
* [npm-test(1)](https://docs.npmjs.com/cli/test)
* [npm-start(1)](https://docs.npmjs.com/cli/start)
* [npm-restart(1)](https://docs.npmjs.com/cli/restart)
* [npm-stop(1)](https://docs.npmjs.com/cli/stop)
