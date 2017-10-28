npm-search(1) -- 搜索包
====================================
基于 [npm-search(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-search.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm search [-l|--long] [--json] [--parseable] [--no-description] [search terms ...]

aliases: s, se, find
```


## DESCRIPTION 描述

在注册表中搜索与关键词匹配的包。`npm search` 通过包元数据对注册表中的所有文件执行线性、增量、词法排序的搜索。如果启用了颜色，它将高亮显示匹配的结果。

此外，使用与更多搜索词配对的 `--searchopts` 和 `--searchexclude` 选项，将分别包括和排除进一步的模式。`--searchopts` 与标准的搜索术语之间的主要区别在于，前者不会高亮显示输出结果，并可用于更细粒度的过滤。另外，这两个选项都可以添加到 `.npmrc` 用于默认的搜索过滤行为。

搜索还允许在搜索结果中定位维护者，通过在 其 npm 用户名前加上 `=`。

如果一个术语以 `/` 开头，那么它会被解释为正则表达式，并支持标准的 JavaScript RegExp 语法。在这种情况下，结尾的 `/` 将被忽略。（请注意，在大多数 shell 中，许多正则表达式字符必须转义或引号包裹。）

### A Note on caching 关于缓存的注意事项

## CONFIGURATION 配置

### description

* 默认：`true`
* 类型：`Boolean`

用作 `--no-description`，禁用搜索匹配包描述，并禁止在结果中显示该字段。

### json

* 默认：`false`
* 类型：`Boolean`

以 JSON 数组输出搜索结果。

### parseable

* 默认：`false`
* 类型：`Boolean`

以 tab 分隔列的行输出搜索结果。

### long

* 默认：`false`
* 类型：`Boolean`

多行显示包的完整描述和其他长文本。当禁用（默认）时，搜索结果会被截断以适合整齐地显示为一行。具有极长名称的模块将会被多行显示。

### searchopts

* 默认：""
* 类型：`String`

始终传递到搜索的空格分隔的选项。

### searchexclude

* 默认： ""
* 类型：`String`

空格分隔的选项来限制搜索结果。

### searchstaleness

* 默认：900（15 分钟）
* 类型：`Number`

在另一个注册表请求之前的缓存的时间（以秒为单位）。

### registry

 * 默认：<https://registry.npmjs.org/>
 * 类型：`url`

搜索指定注册表中的模块。如果你已将 npm 配置为指向其他默认注册表，例如内部专用模块存储库，则在搜索时，`npm search` 将默认搜索该注册表。传递不同的注册表地址，如上面的默认值，来覆盖此设置。

## SEE ALSO 亦可参阅
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-view(1)](https://docs.npmjs.com/cli/view)
