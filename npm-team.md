npm-team(1) --  管理组织团队和团队成员
=============================================================
基于 [npm-team(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-team.md) 官方文档翻译版本


## SYNOPSIS 概要
```bash
npm team create <scope:team>
npm team destroy <scope:team>

npm team add <scope:team> <user>
npm team rm <scope:team> <user>

npm team ls <scope>|<scope:team>

npm team edit <scope:team>
```


## DESCRIPTION 描述

用于管理组织中的团队，并更改团队成员。不处理包的权限。

在团队上运行时，团队始终必须符合所属的组织/作用域，以冒号（`:`）分隔。也就是说，如果在 `foo` 组织中有 `developers` 团队，则必须在这些命令中始终以 `foo：developers` 指向该团队。

* create / destroy：
  创建一个新的团队，或者销毁一个现有的团队。

* add / rm：
  将用户添加到现有团队，或从他们所属的团队中删除用户。

* ls：
  如果在组织名称上执行，将返回该组织下的现有团队列表。如果在一个团队上执行，将返回属于该特定团队的所有用户列表。

## DETAILS 详情

`npm team` 总是直接在当前注册表上运行，可以使用 `--registry = <registry url>` 命令行进行配置。

为了创建团队并管理团队成员，你必须是给定的组织的**团队管理员**。显示团队和团队成员列表可以由组织的任何成员完成。

组织创建、管理员管理和**组织**成员都是通过网页完成的，而不是 npm CLI。

要使用团队来管理组织的包权限，请使用 `npm access` 命令来授予或撤消相应的权限。


## SEE ALSO 亦可参阅

* [npm-access(1)](https://docs.npmjs.com/cli/access)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
