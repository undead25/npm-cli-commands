npm-completion(1) -- 用于 npm TAB 自动补全
===========================================
基于 [npm-completion(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-completion.md) 官方文档翻译版本


## SYNOPSIS 概要
```bash
source <(npm completion)
```


## DESCRIPTION 描述

在所有 npm 命令中启用 tab 自动补全。

上面的概要是将补全操作加载到当前的 `shell` 中。将它添加到 `~/.bashrc` 或 `~/.zshrc` 中将使得补全可以随处使用：

```bash
npm completion >> ~/.bashrc
npm completion >> ~/.zshrc
```

当然，你也可以将 npm 的补全输出为一个文件，比如 `/usr/local/etc/bash_completion.d/npm`，如果你有一个系统会为你读这个文件。

当在环境中定义了 `COMP_CWORD`、`COMP_LINE`、和 `COMP_POINT` 时，`npm completion` 作用在“管道模式”中，并根据参数输出补全。


## SEE ALSO 亦可参阅

* [npm-developers(7)](https://docs.npmjs.com/misc/developers)
* [npm(1)](https://docs.npmjs.com/cli/npm)
