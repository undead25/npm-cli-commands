npm-start(1) -- start 脚本命令
===============================
基于 [npm-start(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-start.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm start [-- <args>]
```


## DESCRIPTION 描述
运行 `package.json` 文件 `"scripts"` 对象中， `"start"` 属性指定的脚本命令。如果没有指定，则运行 `node server.js` 命令。

在 [`npm@2.0.0`](http://blog.npmjs.org/post/98131109725/npm-2-0-0) 中，你可以在执行脚本时使用自定义参数。更多详细信息可以参考 [npm-run-script(1)](https://docs.npmjs.com/cli/run-script)。


## SEE ALSO 亦可参阅
* [npm-run-script(1)](https://docs.npmjs.com/cli/run-script)
* [npm-scripts(7)](https://docs.npmjs.com/misc/scripts)
* [npm-test(1)](https://docs.npmjs.com/cli/test)
* [npm-restart(1)](https://docs.npmjs.com/cli/restart)
* [npm-stop(1)](https://docs.npmjs.com/cli/stop)

