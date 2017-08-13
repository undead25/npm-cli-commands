npm-adduser(1) -- 添加注册表用户帐户
=============================================
基于 [npm-adduser(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-adduser.md) 官方文档翻译版本


## SYNOPSIS 概要
```bash
npm adduser [--registry=url] [--scope=@orgname] [--always-auth] [--auth-type=legacy]

aliases: login, add-user
```


## DESCRIPTION 描述
在指定的注册表中创建或验证名为 `<username>` 的用户，并将凭证保存在 `.npmrc` 文件中。如果未指定注册表，那么将使用默认的注册表（参考 [`npm-config(7)`](https://docs.npmjs.com/misc/config)）

在提示中读取用户名、密码和邮箱。

需要重置密码请转到 <https://www.npmjs.com/forgot>

需要修改邮箱地址请转到 <https://www.npmjs.com/email-edit>

你可以使用同一账户多次使用此命令来授权新的机器。在新机器上进行身份验证时，用户名，密码和邮箱地址必须与现有记录相匹配。

`npm login` 是 `adduser` 的别名，行为方式完全相同。


## CONFIGURATION 配置
### registry 注册表
默认：[https://registry.npmjs.org/](https://registry.npmjs.org/)

npm 包注册表的基本 URL。如果 `scope` 被指定了，那么此注册表仅用于具有该作用域的包。`scope` 默认是你目前所在的项目目录（如果有）。参见 [`npm-scope（7）](https://docs.npmjs.com/misc/scope)`。

### scope 作用域
默认：无

如果指定，那么给定的用户和登录凭证将与指定的作用域相关联。参见 [`npm-scope（7）`](https://docs.npmjs.com/misc/scope))。你可以同时使用，例如：

```bash
npm adduser --registry=http://myregistry.example.com --scope=@myco
```
这将为给定作用域设置注册表，并同时登录或创建该注册表的用户。

### always-auth 始终验证
默认：`false`

如果指定，保存配置意味着对给定注册表的所有请求都将包含授权信息。这适用于私有注册表。也可以配合 `--registry` 和/或 `--scope` 使用，例如：

```bash
npm adduser --registry=http://private-registry.example.com --always-auth
```
这将确保所有对于该注册表（包括用于压缩包）的请求都包含一个授权头。此设置可能需要与私有注册表一起使用，其元数据和包压缩文件存储在不同的主机上。有关 always-auth 的更多详细信息，请参见 [`npm-config（7）`](https://docs.npmjs.com/misc/config) 中的 `always-auth`。 `always-auth` 的注册表特定配置优先于任何全局配置。

### auth-type 验证类型
* 默认：`'legacy'`
* 类型：`'legacy'`、`'sso'`、`'saml'`、`'oauth'`

与 `adduser` /`login` 一起使用何种认证策略。除了传统 npm 中经典的用户名/密码输入外，某些 npm 注册表（例如，npmE）可能会支持备用验证策略。


## SEE ALSO 亦可参阅
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-owner(1)](https://docs.npmjs.com/cli/owner)
* [npm-whoami(1)](https://docs.npmjs.com/cli/whoami)