npm-version(1) -- 打包版本
========================================

## SYNOPSIS 概要
```
npm version [<newversion> | major | minor | patch | premajor | preminor | prepatch | prerelease | from-git]

'npm [-v | --version]' 打印 npm 版本
'npm view <pkg> version' 查看某个包已发布的版本
'npm ls' 检查当前包/依赖包的版本
```


## DESCRIPTION 描述
在包目录中运行这个命令来打包版本并将新的数据写到 `package.json`，如果存在 `npm-shrinkwrap.json`，它也会被更新。

`newversion` 参数应该是一个有效的语义化版本字符串。[semver.inc](https://github.com/npm/node-semver#functions) 第二个有效的参数是 `patch`、`minor`、`major`、`prepatch`、`preminor`、`premajor`、`prerelease` 其中之一或者是 `from-git`。在第二种情况下，会在现有版本的指定字段上加 1。`from-git` 将尝试读取最新的 git 标签，并使用它作为新的 npm 版本。

如果在 git 仓库中运行，它也会创建一个版本提交和标签。这个行为是由 `git-tag-version`（见下面）控制的，可以通过运行 `npm --no-git-tag-version version` 在命令行中禁用它。如果工作目录不整洁，将会失败，除非设置了 `-f` 或者 `force` 标志。

如果提供了 `-m` 或 `--message` 配置选项，npm 将在创建版本提交时将其作为提交信息。如果 `message` 配置包含 `％s`，那么它将被替换为生成的版本号。例如：

```bash
npm version patch -m "Upgrade to %s for reasons"
```

如果设置了 `sign-git-tag` 配置，那么标签将使用 `-s` 标志来进行签名。请注意，你必须在你的 git 配置中设置默认的 GPG 密钥才能正常工作。例如：

```bash
$ npm config set sign-git-tag true
$ npm version patch

You need a passphrase to unlock the secret key for
user: "isaacs (http://blog.izs.me/) <i@izs.me>"
2048-bit RSA key, ID 6C481CF6, created 2010-08-31

Enter passphrase:
```

如果 `preversion`、`version` 或者 `postversion` 在 package.json 的 `scripts` 属性中，它们将作为运行 `npm version` 的一部分被执行。

确切的执行顺序如下：
  1. 开始之前，检查并确保 git 工作目录是干净的。你的脚本可能会在后面的步骤中添加文件到提交中。如果设置了 `--force` 标志，则跳过此步骤。
  2. 运行 `preversion` 脚本。这些脚本可以访问 package.json 中的旧 `version`。典型的用法是在部署之前运行完整的测试套件。你应该使用 `git add` 来明确得添加任何你想要提交的文件。
  3. Bump `version` in `package.json` as requested (`patch`, `minor`, `major`, etc).
  3. 按照要求（`patch`，`minor`，`major`等）在`package.json` 中 `version`。
  4. 运行 `version` 脚本。这些脚本可以访问 package.json 中的新 `version`（例如，将它合并到生成文件的文件头中）。同样，你应该使用 `git add` 来明确得添加任何你想要提交的文件。
  5. 提交并打标签。
  6. 运行 `postversion` 脚本。用它来清理文件系统或者自动推送提交和/或打标签。

看下面的例子：

```json
  "scripts": {
    "preversion": "npm test",
    "version": "npm run build && git add -A dist",
    "postversion": "git push && git push --tags && rm -rf build/temp"
  }
```

这将运行所有的测试，并且只有在它们通过时才会继续。然后运行你的 `build` 脚本，并将 `dist` 目录中的所有内容添加到提交中。提交后，它将新的提交和标签推送到服务器，并删除 `build/temp` 目录。

## CONFIGURATION 配置

### allow-same-version

* 默认：`false`
* 类型：`Boolean`

当使用 `npm version` 将新版本设置为与当前版本相同的值时，阻止错误抛出。

### git-tag-version

* 默认：`true`
* 类型：`Boolean`

提交并给版本更改打标签。

### commit-hooks

* 默认：`true`
* 类型：`Boolean`

提交版本更改时运行 git commit 钩子。

### sign-git-tag

* 默认：`false`
* 类型：`Boolean`

将 `-s` 标志传递给 git 标签。

请注意，你必须在你的 git 配置中设置默认的 GPG 密钥才能正常工作。

## SEE ALSO 亦可参阅
* [npm-init(1)](https://docs.npmjs.com/cli/init)
* [npm-run-script(1)](https://docs.npmjs.com/cli/run-script)
* [npm-scripts(7)](https://docs.npmjs.com/misc/scripts)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
* [semver(7)](https://docs.npmjs.com/misc/semver)
* [config(7)](https://docs.npmjs.com/misc/config)
