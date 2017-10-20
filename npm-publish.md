npm-publish(1) -- 包发布
===================================
基于 [npm-publish(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-publish.md) 官方文档翻译版本


## SYNOPSIS 概要
```bash
npm publish [<tarball>|<folder>] [--tag <tag>] [--access <public|restricted>]

Publishes '.' if no argument supplied
Sets tag 'latest' if no --tag specified
```


## DESCRIPTION 描述

发布一个包到注册表，以便它可以按名称被安装。如果没有本地的 `.gitignore` 或 `.npmignore` 文件存在，则包含目录中的所有文件。如果两个文件都存在，并且文件被`.gitignore` 忽略，而不是 `.npmignore`，那么它将被包含。有关发布的包中包含的内容，以及它是如何构建的详细信息，请参阅 [`npm-developers(7)`](https://docs.npmjs.com/misc/developers)。

默认情况下，npm 将包发布到公共注册表。可以通过指定一个不同的默认注册表或者在名称中使用 [`npm-scope(7)`](https://docs.npmjs.com/misc/scope) 来进行修改（参见 [`package.json(5)`](https://docs.npmjs.com/files/package.json)）。

* `<folder>`：
  包含 package.json 文件的文件夹。

* `<tarball>`:
  指向 gzip 压缩后的 tar 包的 url 或者文件路径，它包含一个有 package.json 文件的文件夹。

* `[--tag <tag>]`
  使用给定的标签注册已发布的包，以便 `npm install <name>@<tag>` 将安装此版本。默认情况下，`npm publish` 更新， `npm install` 安装 `latest` 标签。 有关标签的详细信息，请参见 `[npm-dist-tag(1)](https://docs.npmjs.com/cli/dist-tag)`。

* `[--access <public|restricted>]`
  告知注册表是否应该将该包公开或限制。仅适用于作用域包，默认为 `restricted`。 如果你没有付费帐户，则必须使用 `--access public` 发布作用域包。

如果包名称和版本的组合已经存在于指定的注册表中，则将发布失败。

一旦使用了给定的名称和版本发布包，即使通过 [`npm-unpublish(1)`](https://docs.npmjs.com/cli/unpublish) 删除了该名称和版本的组合，它也不能被再次使用。

从 `npm@5` 开始，压缩包的 sha1sum 和一个带有 sha512sum 的完整性字段将在发布过程中提交给注册表。随后的安装将使用最强支持的算法来验证下载。

除了发布到实际的注册表之外，“模拟运行”做了所有发布的事情，请参阅 [`npm-pack(1)`](https://docs.npmjs.com/cli/pack)，显示要包括的文件，并将其打包到要上传到注册表的压缩包中。


## SEE ALSO 亦可参阅
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-scope(7)](https://docs.npmjs.com/misc/scope)
* [npm-adduser(1)](https://docs.npmjs.com/cli/adduser)
* [npm-owner(1)](https://docs.npmjs.com/cli/owner)
* [npm-deprecate(1)](https://docs.npmjs.com/cli/deprecate)
* [npm-dist-tag(1)](https://docs.npmjs.com/cli/dist-tag)
* [npm-pack(1)](https://docs.npmjs.com/cli/pack)
