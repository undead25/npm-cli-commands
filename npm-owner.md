npm-owner(1) -- 管理包拥有者
=====================================
基于 [npm-owner(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-owner.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm owner add <user> [<@scope>/]<pkg>
npm owner rm <user> [<@scope>/]<pkg>
npm owner ls [<@scope>/]<pkg>

aliases: author
```


## DESCRIPTION 描述

管理已发布包的所有权。

* `ls`：
  列出所有有权修改包并推送新版本的用户。方便你知道谁来帮忙解决 bug。

* `add`：
  添加新用户作为包的维护者。该用户可以修改元数据，发布新版本，并添加其他所有者。

* `rm`：
  从包所有者列表中删除用户。这将立即撤销他们的权限。

请注意，这里只有一个级别的访问，要么可以修改包，要么不能。未来的版本可能包含更多细粒度的访问级别，但是目前还没有实现。

## SEE ALSO 亦可参阅

* [npm-publish(1)](https://docs.npmjs.com/cli/publish)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-adduser(1)](https://docs.npmjs.com/cli/adduser)
* [npm-disputes(7)](https://docs.npmjs.com/misc/disputes)
