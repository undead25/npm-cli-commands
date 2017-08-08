npm-access(1) -- 在发布的包上设置访问级别
=======================================================
基于[npm-access(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-access.md) 官方文档翻译版本

译者注：访问级别指的是包的读写权限，**只读** 或者 **读写**，对应为`read-only` | `read-write`

## SYNOPSIS 概要
```bash
npm access public [<package>]
npm access restricted [<package>]

npm access grant <read-only|read-write> <scope:team> [<package>]
npm access revoke <scope:team> [<package>]

npm access ls-packages [<user>|<scope>|<scope:team>]
npm access ls-collaborators [<package> [<user>]]
npm access edit [<package>]
```


## DESCRIPTION 描述
用于设置私有包的访问控制

对于所有的子命令，如果没有带包名，那么 `npm acccess` 的操作将在当前工作目录的包中执行。

* `public` / `restricted`:
  设置一个包是公开访问的还是受限的。
* `grant` / `revoke`:
  添加或删除用户和团队对于包的读写权限。
* `ls-packages`:
  显示用户或组能够访问的所有包以及其访问级别，除了只读公共包（它不会打印整个注册列表）。
* `ls-collaborators`: 
  显示包的所有访问权限。这将显示你至少有只读权限的包。如果 `<user>`这个参数传入，那这个列表将过滤只属于该用户、组的包。
* `edit`:
  使用 `$EDITOR` 为一个包设置访问权限。


## DETAILS 详解
`npm access` 总是直接作用于当前注册表，在命令行使用 `--registry=<registry url>` 进行配置。

无作用域包*始终是公开的*。
(译者注：作用域包和非作用域包说明请参考[npm-scope(7)](https://docs.npmjs.com/misc/scope))

作用域包*默认是受限制的*，但是你也可以使用 `npm publish --access=public` 命令来发布它们，或者在它们被初次发布后使用 `npm access public` 命令来将其的访问权限设置为公开。
（译者注：例如 `@angular/core` 这个包就是作用域包设置为公开）

你必须有设置包的访问权限：
* 你是无作用域或作用域包的所有者。
* 你是拥有作用域的团队成员。
* 你已获得包的读写权限，无论是作为一个团队的一员，或是其所有者。

如果你的帐户没有支付（译者注：`private modules` 付费用户），除非你使用 `--access=public`命令，否则在你尝试发布作用域包时
将会失败，并带有 `HTTP 402` 状态码（逻辑上允许的情况下）。

团队和团队成员的管理是通过 `npm team` 命令完成的。

## SEE ALSO 请参阅
* [npm-team(1)](https://docs.npmjs.com/cli/team)
* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-scope(7)](https://docs.npmjs.com/misc/scope) (译者注)
