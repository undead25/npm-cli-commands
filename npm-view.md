npm-view(1) -- 查看注册表信息
=================================
基于 [npm-view(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-view.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm view [<@scope>/]<name>[@<version>] [<field>[.<subfield>]...]

aliases: info, show, v
```


## DESCRIPTION 描述
此命令显示有关包的数据，并将其打印到 `outfd` 配置引用的流中，默认为 `stdout`。

要显示 `connect` 的包注册表项，可以这样：
```bash
npm view connect
```

如果未指定，默认版本是 `latest`。

可以在包描述符之后指定字段名称。例如，要显示 `ronn` 0.3.5 版本的依赖关系，可以执行以下操作：
```bash
npm view ronn@0.3.5 dependencies
```

你可以通过点号将它们分开来查看子字段。要查看 `npm` 最新版本的 `git URL`，可以执行以下操作：
```bash
npm view npm repository.url
```

这使得我们可以通过一些 shell 脚本来查看相关依赖关系。例如，要查看 `ronn` 所依赖的关于 `opts` 版本的所有数据，可以执行以下操作：

```bash
npm view opts@$(npm view ronn dependencies.opts)
```

对于数组字段，请求非数字字段将从列表中的对象返回所有值。例如，要获取 `express` 项目所有贡献者的名称，可以这样：

```bash
npm view express contributors.email
```

你还可以使用方括号中的数字索引来选择数组字段中的特定的项。要获取列表中第一个贡献者的邮箱地址，可以执行以下操作：
```bash
npm view express contributors[0].email
```

可以指定多个字段，并将一个接一个地进行打印。例如，要获取所有的贡献者姓名和邮箱地址，可以这样做：
```bash
npm view express contributors.name contributors.email
```

如果它们作为一个对象展示，那 `Person` 字段会被显示为一个字符串。例如，下方的命令将以缩短的字符串格式展示 npm 贡献者的列表。（有关更多信息，请参阅 [`package.json(5)`](https://docs.npmjs.com/files/package.json)。）
```bash
npm view npm contributors
```

如果提供了一个版本范围，那么每个匹配版本包数据将被打印。下方的命令将显示每个匹配版本的 `yui3` 依赖哪个版本的 `jsdom`：
```bash
npm view yui3@'>0.5.4' dependencies.jsdom
```

要显示 `connect` 包的版本历史记录，可以这样：
```bash
npm view connect versions
```


## OUTPUT 输出

如果仅输出单个版本的单个字符串字段，则不会将其着色或用引号括起来，以便将输出管道输出到另一个命令。如果该字段是一个对象，那它将作为JavaScript 对象文字输出。

如果给出了 `--json` 标志，输出的字段将以 JSON 格式展示。

如果版本范围匹配多个版本，则每个打印值将以其适用的版本作为前缀。

如果请求了多个字段，那么它们都带有字段名称。

## SEE ALSO 亦可参阅
* [npm-search(1)](https://docs.npmjs.com/cli/search)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-docs(1)](https://docs.npmjs.com/cli/docs)
