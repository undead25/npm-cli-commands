npm-restart(1) -- 运行包的 `restart` 脚本命令
===================================
基于 [npm-restart(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-restart.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm restart [-- <args>]
```


## DESCRIPTION 描述
运行包的 `restart` 脚本命令。

这将运行包的 `stop`、`restart`、和 `start` 脚本，并会按照下方的顺序运行 `pre-` 和 `post-` 脚本。

1. prerestart
2. prestop
3. stop
4. poststop
5. restart
6. prestart
7. start
8. poststart
9. postrestart

## NOTE 注意事项

请注意，`restart` 脚本**只是**运行 `stop` 和 `start` 脚本，而不是替换它们。

这是 `npm` v2 的行为。此行为将随着主版本号的增加而改变。

## SEE ALSO 亦可参阅
* [npm-run-script(1)](https://docs.npmjs.com/cli/run-script)
* [npm-scripts(7)](https://docs.npmjs.com/misc/scripts)
* [npm-test(1)](https://docs.npmjs.com/cli/test)
* [npm-star(1)](https://docs.npmjs.com/cli/start)
* [npm-stop(1)](https://docs.npmjs.com/cli/stop)
* [npm-restart(1)](https://docs.npmjs.com/cli/restart)
