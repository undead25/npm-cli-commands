npm-logout(1) -- 登出注册表
========================================
基于 [npm-logout(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-logout.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm logout [--registry=<url>] [--scope=<@scope>]
```


## DESCRIPTION 描述
当登录到支持基于令牌进行身份验证的注册表时，告诉服务器结束该令牌的会话。这将使得所有地方你使用的令牌无效，而不仅仅是针对当前的环境。

当登录到使用用户名和密码进行身份验证的旧版注册表时，这将清除用户配置中的凭据。在这种情况下，它**只**影响当前的环境。

如果提供了 `--scope` 参数，这将找到连接到该作用域注册表的凭据。



## CONFIGURATION 配置
### registry 注册表

默认：https://registry.npmjs.org/

npm 包注册表的基本 URL。如果指定了 `scope`，则优先。

### scope 作用域
默认：若果有，表示当前项目的作用域，否则没有。

如果指定了，则登出指定的作用域。参见 `[npm-scope(7)]`(https://docs.npmjs.com/misc/config)。
```bash
npm logout --scope=@myco
```

## SEE ALSO 亦可参阅
* [npm-adduser(1)](https://docs.npmjs.com/cli/adduser)
* [npm-registry(7)](https://docs.npmjs.com/misc/registry)
* [npm-config(1)](https://docs.npmjs.com/cli/config)
* [npm-config(7)](https://docs.npmjs.com/misc/config)
* [npmrc(5)](https://docs.npmjs.com/files/npmrc)
* [npm-whoami(1)](https://docs.npmjs.com/cli/whoami)
