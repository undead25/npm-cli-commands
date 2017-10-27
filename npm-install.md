npm-install(1) -- 安装包
===================================

## SYNOPSIS 概要
```bash
npm install (with no args, in package dir)
npm install [<@scope>/]<name>
npm install [<@scope>/]<name>@<tag>
npm install [<@scope>/]<name>@<version>
npm install [<@scope>/]<name>@<version range>
npm install <git-host>:<git-user>/<repo-name>
npm install <git repo url>
npm install <tarball file>
npm install <tarball url>
npm install <folder>

alias: npm i
common options: [-P|--save-prod|-D|--save-dev|-O|--save-optional] [-E|--save-exact] [-B|--save-bundle] [--no-save] [--dry-run]
```


## DESCRIPTION 描述
此命令将安装一个包，以及所有它依赖的包。如果这个包有一个 `package-lock` 或者 `shrinkwrap` 文件，则依赖关系的安装将被它们驱动，如果两个文件都存在，那么优先 `npm-shrinkwrap.json`。请参阅 [package-lock.json(5)](https://docs.npmjs.com/files/package-lock.json) 和 [npm-shrinkwrap(1)](https://docs.npmjs.com/cli/shrinkwrap)。

`package` 指的是：
* a) 一个包含由 [`package.json(5)`](https://docs.npmjs.com/files/package.json) 描述的程序文件夹
* b) 一个包含 (a) 的压缩包
* c) 一个解析 (b) 的 url
* d) 一个通过 (c) 发布在注册表上的 `<name>@<version>`（参见 [`npm-registry(7)`](https://docs.npmjs.com/misc/registry)）
* e) 一个指向 (d) 的 `<name>@<tag>`（参见 [`npm-dist-tag(1)`](https://docs.npmjs.com/cli/dist-tag)）
* f) 一个带有“latest”标签且满足（e）的 `<name>`
* g) 一个解析 (a) 的 `<git remote url>`

即使你从未发布过包，如果你只是想编写一个 node 程序 (a)，你也能从使用 npm 中受益。你也可能需要在把它打进压缩包 (b) 之后能够很容易地将其安装到别的地方。

* `npm install` （在包根目录下，不带参数）：

    在本地 node_modules 文件夹中安装依赖项。

    在全局模式下（即命令带有 `-g` 或 `--global`），它将当前的包上下文（即当前工作目录）作为全局包安装。

    默认情况下，`npm install` 会把所有 `package.json(5)` 中列出的模块作为依赖进行安装。

    使用 `--production` 标志（或 `NODE_ENV` 环境变量设置为 `production` 时），npm 将不会安装 `devDependencies` 中列出的模块。

* `npm install <folder>`：

  将目录中的包作为当前项目的软连接进行安装，它的依赖关系将在链接之前被安装。如果 `<folder>` 位于项目的根目录中，那它的依赖关系可能会被提升到 `node_modules` 的顶层，就像其他类型的依赖一样。

* `npm install <tarball file>`：

    安装一个位于文件系统上的包。注意：如果你只是将 dev 目录链接到 npm 根目录，使用 `npm link` 会更方便。文件名**必须**使用 `.tar`，`.tar.gz` 或 `.tgz` 作为扩展名。

    示例：
    ```bash
    npm install ./package.tgz
    ```

* `npm install <tarball url>`:

    请求压缩包的 url，然后安装它。为了区分其他选项，参数必须以 `http：//` 或 `https：//` 开头。

    示例：
    ```bash
    npm install https://github.com/indexzero/forever/tarball/v0.5.6
    ```
    
* `npm install [<@scope>/]<name>`:

    进行 `<name>@<tag>` 安装，其中 `<tag>` 是 `tag` 配置。 （参见 [`npm-config(7)`](https://docs.npmjs.com/misc/config)，配置的默认值为 `latest`）

    在大多数情况下，将安装 npm 注册表中标有 `latest` 的模块版本。

    示例：
    ```bash
    npm install sax
    ```

    `npm install` 默认将所有指定的包保存到 `dependencies` 中。此外，你可以使用一些其他标记来控制保存位置和方式：

    * `-P, --save-prod`：包将出现在 `dependencies` 中。 除非带有 `-D` 或 `-O`，这是默认配置。

    * `-D, --save-dev`：包将出现在 `devDependencies` 中。

    * `-O, --save-optional`：包将出现在 `optionalDependencies` 中。

    * `--no-save`：阻止保存到 `dependencies` 中。

    当使用上面的选项将依赖关系保存到 package.json 时，还有两个可选的标志：

    * `-E, --save-exact`：将给保存的依赖关系配置一个确切的版本，而不是使用 npm 的默认的语义化版本。

    * `-B, --save-bundle`：保存的依赖项也将添加到 `bundleDependencies` 列表中。

    此外，如果你有一个 `npm-shrinkwrap.json` 或者 `package-lock.json`，那么它也会被更新。

    `<scope>` 是可选的。包将从指定作用域关联的注册表中下载。如果没有注册表与给定的作用域相关联，则假定使用默认注册表。参见 [`npm-scope(7)`](https://docs.npmjs.com/misc/scope)。

    注意：如果作用域名称中没有包含 `@` 符号，那么 npm 会将其解释为 GitHub 仓库，请参见下文。作用域名称也必须后跟斜杠。

    示例：
    ```bash
    npm install sax
    npm install githubname/reponame
    npm install @myorg/privatepackage
    npm install node-tap --save-dev
    npm install dtrace-provider --save-optional
    npm install readable-stream --save-exact
    npm install ansi-regex --save-bundle
    ```

    **注意**：如果在当前工作目录中有一个名为 `<name>` 的文件或文件夹，那么它将尝试安装该文件或文件夹，并且只有在无效的情况下才尝试通过名称请求获取这个包。

* `npm install [<@scope>/]<name>@<tag>`:

    安装指定标签引用的包版本。如果标签在该包的注册表数据中不存在，那么将安装失败。

    示例：
    ```bash
    npm install sax@latest
    npm install @myorg/mypackage@latest
    ```

* `npm install [<@scope>/]<name>@<version>`:

    安装指定版本的包。 如果版本尚未发布到注册表，则将安装失败。

    示例：
    ```bash
    npm install sax@0.1.1
    npm install @myorg/privatepackage@1.5.0
    ```

* `npm install [<@scope>/]<name>@<version range>`:

    安装与匹配指定版本范围的包版本。遵循解析 [`package.json(5)`](https://docs.npmjs.com/files/package.json) 中描述的依赖关系相同的规则。

    请注意，大多数版本范围必须用引号括起来，以便 shell 将其视为单个参数。

    示例：
    ```bash
    npm install sax@">=0.1.0 <0.2.0"
    npm install @myorg/privatepackage@">=0.1.0 <0.2.0"
    ```

* `npm install <git remote url>`:

    通过 `git` 克隆安装 git 上托管的包。只适用于完整的远程 git URL。

    ```bash
    <protocol>://[<user>[:<password>]@]<hostname>[:<port>][:][/]<path>[#<commit-ish> | #semver:<semver>]
    ```
 
    `<protocol>` 是 `git`、`git+ssh`、`git+http`、`git+https` 或者 `git+file` 其中的一个。

    如果提供了 `#<commit-ish>`，它将被用来完全克隆该提交。如果 `commit-ish` 是 `#semver:<semver>` 格式， 那 `<semver>` 可以是任何有效的语义化版本范围或者是确切的版本，npm 将在远程仓库中查找与该范围匹配的任何标签或引用，就像注册表依赖一样。如果没有指定 `#<commit-ish>` 或者 `#semver:<semver>`，那么会使用 `master`。

    如果仓库使用子模块，那么这些子模块也将被克隆。

    如果正在安装的包中包含一个 `prepare` 脚本，那么在打包和安装之前，其 `dependencies` 和 `devDependencies` 会被安装，脚本将被运行。

    npm 识别以下 git 环境变量，并在运行 git 时添加到环境中：

    * `GIT_ASKPASS`
    * `GIT_EXEC_PATH`
    * `GIT_PROXY_COMMAND`
    * `GIT_SSH`
    * `GIT_SSH_COMMAND`
    * `GIT_SSL_CAINFO`
    * `GIT_SSL_NO_VERIFY`

    更多详细信息请参考 git 手册。

    示例：
    ```bash
    npm install git+ssh://git@github.com:npm/npm.git#v1.0.27
    npm install git+ssh://git@github.com:npm/npm#semver:^5.0
    npm install git+https://isaacs@github.com/npm/npm.git
    npm install git://github.com/npm/npm.git#v1.0.27
    GIT_SSH_COMMAND='ssh -i ~/.ssh/custom_ident' npm install git+ssh://git@github.com:npm/npm.git
    ```

* `npm install <githubname>/<githubrepo>[#<commit-ish>]`：
* `npm install github:<githubname>/<githubrepo>[#<commit-ish>]`：

    通过尝试使用 `git` 克隆来安装在 `https://github.com/githubname/githubrepo` 上的包。

    如果提供了 `#<commit-ish>`，它将被用来完全克隆该提交。如果 `commit-ish` 是 `#semver:<semver>` 格式， 那 `<semver>` 可以是任何有效的语义化版本范围或者是确切的版本，npm 将在远程仓库中查找与该范围匹配的任何标签或引用，就像注册表依赖一样。如果没有指定 `#<commit-ish>` 或者 `#semver:<semver>`，那么会使用 `master`。

    与常规的 git 依赖关系一样，如果包具有 `prepare` 脚本，则在安装包之前会安装 `dependencies` 和 `devDependencies`。
    

    示例：
    ```bash
    npm install mygithubuser/myproject
    npm install github:mygithubuser/myproject
    ```

* `npm install gist:[<githubname>/]<gistID>[#<commit-ish>|#semver:<semver>]`：

    通过尝试使用 `git` 克隆来安装在 `https://gist.github.com/gistID` 上的包。与 gist 相关联的 GitHub 用户名是可选的，不会保存在 `package.json`中。    

    与常规的 git 依赖关系一样，如果包具有 `prepare` 脚本，则在安装包之前会安装 `dependencies` 和 `devDependencies`。

    示例：
    ```bash
    npm install gist:101a11beef
    ```

* `npm install bitbucket:<bitbucketname>/<bitbucketrepo>[#<commit-ish>]`：

    通过尝试使用 `git` 克隆来安装在 `https://bitbucket.org/bitbucketname/bitbucketrepo` 上的包。

    如果提供了 `#<commit-ish>`，它将被用来完全克隆该提交。如果 `commit-ish` 是 `#semver:<semver>` 格式， 那 `<semver>` 可以是任何有效的语义化版本范围或者是确切的版本，npm 将在远程仓库中查找与该范围匹配的任何标签或引用，就像注册表依赖一样。如果没有指定 `#<commit-ish>` 或者 `#semver:<semver>`，那么会使用 `master`。

    与常规的 git 依赖关系一样，如果包具有 `prepare` 脚本，则在安装包之前会安装 `dependencies` 和 `devDependencies`。

    示例：
    ```bash
    npm install bitbucket:mybitbucketuser/myproject
    ```

* `npm install gitlab:<gitlabname>/<gitlabrepo>[#<commit-ish>]`:

    通过尝试使用 `git` 克隆来安装在 `https://gitlab.com/gitlabname/gitlabrepo` 上的包。

    如果提供了 `#<commit-ish>`，它将被用来完全克隆该提交。如果 `commit-ish` 是 `#semver:<semver>` 格式， 那 `<semver>` 可以是任何有效的语义化版本范围或者是确切的版本，npm 将在远程仓库中查找与该范围匹配的任何标签或引用，就像注册表依赖一样。如果没有指定 `#<commit-ish>` 或者 `#semver:<semver>`，那么会使用 `master`。

    与常规的 git 依赖关系一样，如果包具有 `prepare` 脚本，则在安装包之前会安装 `dependencies` 和 `devDependencies`。

    示例：
    ```bash
    npm install gitlab:mygitlabuser/myproject
    npm install gitlab:myusr/myproj#semver:^5.0
    ```

你可以组合多个参数，甚至多个类型的参数。
例如：
```bash
npm install sax@">=0.1.0 <0.2.0" bench supervisor
```

`--tag` 参数适用于所有指定的安装目标。如果存在具有给定名称的标签，则会优先安装此版本。

`--dry-run` 参数将以平常的方式报告，安装会在实际没有安装任何内容的情况下完成。

即使磁盘上存在本地副本，`-f` 或 `--force` 参数也将使得 npm 获取远程资源。
```bash
npm install sax --force
```

`-g` 或 `--global` 参数将使得 npm 在全局而不是本地进行包的安装。请参阅 [`npm-folders(5)`](https://docs.npmjs.com/files/folders)。

`--global-style` 参数将使得 npm 将包安装到本地的 `node_modules` 文件夹中，它与全局 `node_modules` 文件夹使用相同的布局。只有直接依赖关系会显示在 `node_modules`中，而他们所依赖的所有东西都会平级展示在 `node_modules` 文件夹中。这显然会排除一些删除的重复数据。

`--ignore-scripts` 参数将使得 npm 不执行 `package.json` 中定义的任何脚本。请参阅 [`npm-scripts(7)`](https://docs.npmjs.com/misc/scripts)。

`--legacy-bundling` 参数将使得 1.4 之前的 npm 版本（如 node 0.8 附带的版本）可以安装该软件包。这排除了所有自动删除的重复数据。

`--link` 参数会使得 npm 在一些情况下将全局安装的包链接到本地空间。

`--no-bin-links` 参数将阻止 npm 为包可能包含的任何二进制文件创建软链接。

`--no-optional` 参数将阻止可选依赖关系的安装。

`--no-shrinkwrap` 参数将忽略可用的包锁定或 shrinkwrap 文件，并改用 `package.json`。

`--no-package-lock` 参数会阻止 npm 创建 `package-lock.json` 文件。

`--nodedir=/path/to/node/source` 参数将允许 npm 找到 node 源代码以便 npm 可以编译本地模块。

`--only={prod[uction]|dev[elopment]}` 参数将使得只有 `devDependencies` 或只有非 `devDependencies` 被安装，而忽略 `NODE_ENV`。

请参见 [`npm-config(7)`](https://docs.npmjs.com/misc/config)。很多配置参数对安装都有一些影响，因为这是 npm 的大部分功能。

## ALGORITHM 算法

npm 使用以下算法进行包的安装：
```bash
从磁盘上加载现有的 `node_modules` 树
克隆树
获取 `package.json` 和各种元数据并将其添加到克隆中
检测克隆并添加任何缺少的依赖关系
  依赖关系的添加将尽可能地接近顶部而不会破坏任何其他模块
将原始树与克隆的树进行比较，并列出要将其转换为另一个的操作
执行所有操作，先执行最深的
  这些操作是安装，更新，删除和移动
```

对于 `package{dep}` 结构：`A{B,C}, B{C}, C{D}`，这个算法会产生：

```bash
A
+-- B
+-- C
+-- D
```

也就是说，A 已经将 C 安装在了更高的层级上，这满足 B 和 C 的依赖关系。因为没有任何冲突，D 仍然安装在了顶层。

对于 `A{B,C}, B{C,D@1}, C{D@2}`，这个算法会产生：
```bash
A
+-- B
+-- C
   `-- D@2
+-- D@1
```
由于 B 依赖的 D@1 将被安装在顶层，所以 C 必须自己安装 D@2。该算法是确定的，但是如果要求以不同顺序安装两个依赖关系，则可能会生成不同的树。

有关 npm 创建的特定文件夹结构的更详细说明，请参阅 [`npm-folders(5)`](https://docs.npmjs.com/files/folders)。

### npm 的安装算法的限制

npm 将拒绝安装与当前包相同名称的任何包。这可以用 `--force` 标志来解决，但是在大多数情况下可以通过更改本地包名称来解决。

有一些非常罕见和病态的边缘情况，一个循环可能导致 npm 尝试安装一个永无止尽的包树。下面是一个最简单的例子：
```bash
A -> B -> A' -> B' -> A -> B -> A' -> B' -> A -> ...
```

其中 `A` 是一个包的某个版本，`A'` 是同一个包的不同版本。因为 B 依赖于没有在树中的不同版本的 `A`，所以它必须安装一个单独的副本。`A'` 也是如此，它必须安装 `B'`。因为 `B'` 依赖已经被覆盖的 `A` 的原始版本，所以循环是无限的递归。

为了避免这种情况，npm flat-out 拒绝安装任何已经存在于包文件夹祖先树中的任何 `name@version` 版本。更正确但更复杂的解决方案是将现有版本符号链接到新位置。如果这影响到实际的用例，那这个方案将被研究。

## SEE ALSO 亦可参阅
* [npm-folders(5)](https://docs.npmjs.com/files/folders)
* [npm-update(1)](https://docs.npmjs.com/cli/update)
* [npm-link(1)](https://docs.npmjs.com/cli/link)
* [npm-rebuild(1)](https://docs.npmjs.com/cli/rebuild)
* [npm-scripts(7)](https://docs.npmjs.com/misc/scripts)
* [npm-build(1)](https://docs.npmjs.com/cli/build)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-dist-tag(1)](https://docs.npmjs.com/cli/dist-tag)
* [npm-uninstall(1)](https://docs.npmjs.com/cli/uninstall)
* [npm-shrinkwrap(1)](https://docs.npmjs.com/cli/shrinkwrap)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
