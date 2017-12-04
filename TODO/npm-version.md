npm-version(1) -- 控制包版本？
========================================

## SYNOPSIS 概要
```
npm version [<newversion> | major | minor | patch | premajor | preminor | prepatch | prerelease | from-git]

'npm [-v | --version]' to print npm version
'npm view <pkg> version' to view a package's published version
'npm ls' to inspect current package/dependency versions
```


## DESCRIPTION 描述
Run this in a package directory to bump the version and write the new data back to `package.json` and, if present, `npm-shrinkwrap.json`.
在包目录中运行这个命令来打包版本并将新的数据写到 `package.json`，如果存在的话 `npm-shrinkwrap.json`？。

`newversion` 参数应该是一个有效的语义化版本字符串。[semver.inc](https://github.com/npm/node-semver#functions) 第二个有效的参数是 `patch`、`minor`、`major`、`prepatch`、`preminor`、`premajor`、`prerelease` 其中之一或者 `from-git`。在第二种情况下，会在现有版本的指定字段上加 1。`from-git` 将尝试读取最新的 git 标签，并使用它作为新的 npm 版本。

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

The exact order of execution is as follows:
  1. Check to make sure the git working directory is clean before we get started. Your scripts may add files to the commit in future steps. This step is skipped if the `--force` flag is set.
  2. Run the `preversion` script. These scripts have access to the old `version` in package.json. A typical use would be running your full test suite before deploying. Any files you want added to the commit should be explicitly added using `git add`.
  3. Bump `version` in `package.json` as requested (`patch`, `minor`, `major`, etc).
  4. Run the `version` script. These scripts have access to the new `version` in package.json (so they can incorporate it into file headers in generated files for example). Again, scripts should explicitly add generated files to the commit using `git add`.
  5. Commit and tag.
  6. Run the `postversion` script. Use it to clean up the file system or automatically push the commit and/or tag.

看下面的例子：

```json
  "scripts": {
    "preversion": "npm test",
    "version": "npm run build && git add -A dist",
    "postversion": "git push && git push --tags && rm -rf build/temp"
  }
```

This runs all your tests, and proceeds only if they pass. Then runs your `build` script, and adds everything in the `dist` directory to the commit. After the commit, it pushes the new commit and tag up to the server, and deletes the `build/temp` directory.

## CONFIGURATION 配置

### allow-same-version

* Default: false
* Type: Boolean

Prevents throwing an error when `npm version` is used to set the new version to the same value as the current version.

### git-tag-version

* Default: true
* Type: Boolean

Commit and tag the version change.

### commit-hooks

* Default: true
* Type: Boolean

Run git commit hooks when committing the version change.

### sign-git-tag

* Default: false
* Type: Boolean

Pass the `-s` flag to git to sign the tag.

Note that you must have a default GPG key set up in your git config for this to work properly.

## SEE ALSO 亦可参阅
* [npm-init(1)](https://docs.npmjs.com/cli/init)
* [npm-run-script(1)](https://docs.npmjs.com/cli/run-script)
* [npm-scripts(7)](https://docs.npmjs.com/misc/scripts)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
* [semver(7)](https://docs.npmjs.com/misc/semver)
* [config(7)](https://docs.npmjs.com/misc/config)
