npm-doctor(1) -- 检查你的环境
========================================================

## SYNOPSIS 概要
```
npm doctor
```

## DESCRIPTION 描述

`npm doctor` 运行一系列检查来确保 npm 安装了你的 JavaScript 包所需要的东西。npm 主要是一个独立的工具，但它有一些必须要满足的基本需求：

- Node.js 和 git 必须可以由 npm 执行。
- 主要 npm 注册表，`registry.npmjs.com` 或其他使用注册表 API 的可用服务。
- npm 使用的目录，`node_modules`（本地和全局）都存在，并且可以由当前用户写入。
- npm 缓存存在，并且里面的包的压缩包没有损坏。

这些工作异常，npm 可能无法正常工作。很多问题通常都是由 npm 代码之外的东西引起的，所以 `npm doctor` 来确认 npm 的安装状态良好。

除此之外，使用旧版本的 npm 也会有很多问题报告。由于 npm 不断更新，所以运行 `npm@latest` 会比使用旧版本更好。

`npm doctor` 会检查环境中下方列出的项，如果有推荐的变更也会显示。

### `npm ping`

默认情况下，npm 从主 npm 注册表 `registry.npmjs.org` 安装。`npm doctor` 在注册表中调一个特殊的 ping 端点。这也可以用 `npm ping` 来检查。如果此检查失败，则你可能需要配置正在使用的代理，或者与 IT 人员沟通，才能通过 HTTPS 访问 `registry.npmjs.org`。

这个检查是根据你配置的注册表来完成的（你可以通过运行 `npm config get registry` 来看看是什么），如果你使用的注册表不支持主注册表支持的 `/whoami` 端点，这个检查可能会失败。

### `npm -v`

虽然 Node.js 可能捆绑了特定版本的 npm，但是我们建议所有用户运行 npm@latest，这是 CLI 团队的策略。由于 CLI 是由一小部分贡献者维护的，因此只有单一的开发资源，所以 npm 自己长期支持的版本通常只能得到重要的安全性和回归修复。该团队认为，最新测试过的 npm 版本几乎总是功能最强大，无瑕疵的版本。

### `node -v`

对于大多数用户来说，在大多数情况下，最好的 Node 版本将是最新的长期支持（LTS）版本。那些想要访问新的 ECMAscript 特性或对 Node 的标准库进行最新改动的用户可能正在运行一个更加新的版本上，并且由于企业变更控制策略的原因，可能会要求运行旧版本的 Node。没关系！但总的来说，npm 团队建议大多数用户使用 Node.js LTS。

### `npm config get registry`

有些人可能会从项目或者公司的私有包注册表中安装。那很棒！有些人可能会跟随教程或者 StackOverflow 上的问题，来解决可能遇到的问题。有时候，这可能需要改变你指向的注册表。`npm doctor` 只是让你知道你没有使用默认的注册表。

### `which git`

尽管在自述文件中有记录，但可能并不明显的是 npm 需要安装 Git 来完成许多事情。另外，在某些情况下（特别是在 Windows 上），你可能会将 Git 设置为无法通过 `PATH` 访问，以便 npm 可以找到它。这个检查确保 Git 可用。

### 权限检查

* 运行 npm 的用户必须可以读取和写入缓存。
* 运行 npm 的用户必须可以写入全局包二进制文件。
* 如果你在项目目录中运行 `npm doctor`，运行 npm 的用户可以可以读写本地 `node_modules` 目录。

### 验证缓存包的校验

发布 npm 包时，发布过程会生成一个校验和，npm 会在安装时使用它来验证包在传输过程中是否损坏。`npm doctor` 使用这些校验和来验证本地缓存中的包压缩文件（你可以通过 `npm config get cache` 看到这个缓存的位置，然后用 `npm cache ls` 来查看缓存里有什么 —— 可能会超过你的预期！）。如果缓存中存在损坏的包，则应该运行`npm cache clean` 并重置缓存。

## SEE ALSO 亦可参阅
* [npm-bugs(1)](https://docs.npmjs.com/cli/bugs)
* [npm-help(1)](https://docs.npmjs.com/cli/help)
* [npm-ping(1)](https://docs.npmjs.com/cli/ping)
