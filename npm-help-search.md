npm-help-search(1) -- 搜索 npm 帮助文档
===================================================
基于 [npm-help-search(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-help-search.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm help-search <text>
```


## DESCRIPTION 描述
该命令将搜索 npm markdown 文档文件中提供的术语，然后列出结果，按相关性排序。

如果只找到一个结果，那么它将显示帮助主题。

如果 `npm help` 的参数不是一个已知的帮助主题，那么它将调用 `help-search`。很少有必要直接调用这个命令。

## CONFIGURATION 配置
### long 长度
* 类型：`Boolean`
* 默认：`false`

如果为 `true`，"long" 标志将导致输出在文档中找到术语位置的上下文。

如果为 `false`，那么它将列出找到的的帮助主题。

## SEE ALSO 亦可参阅

* [npm(1)](https://docs.npmjs.com/cli/npm)
* [npm-help(1)](https://docs.npmjs.com/cli/help)
