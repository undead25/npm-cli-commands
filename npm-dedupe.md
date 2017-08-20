npm-dedupe(1) -- 减少重复
===================================
基于 [npm-dedupe(1)](https://github.com/npm/npm/blob/latest/doc/cli/npm-dedupe.md) 官方文档翻译版本

## SYNOPSIS 概要
```bash
npm dedupe
npm ddp

aliases: find-dupes, ddp
```

## DESCRIPTION 描述

搜索本地包树，并尝试通过在树上进一步移动依赖关系来简化整体结构，从而可以通过多个依赖包来更有效地共享它们。

例如，考虑这个依赖图：
```bash
a
+-- b <-- depends on c@1.0.x
|   `-- c@1.0.3
`-- d <-- depends on c@~1.0.9
    `-- c@1.0.10
```

在这种情况下，`npm-dedupe(1)` 将树变换为：
```bash
a
+-- b
+-- d
`-- c@1.0.10
```

由于 node 模块查找的层次性，b 和 d 都将通过树的根级别的 c 包来满足其依赖性。

重复数据删除算法遍历树，即使没有找到重复数据，它也尽可能将树中的每个依赖关系移到树中。这将产生一个一维和无重复数据的树。

如果在树中的目标位置上存在合适的版本，那么它将保持不变，但其他重复项将被删除。

参数被忽略了。重复数据删除总是对整个树进行操作。

模块

请注意，此操作会转换依赖关系树，但不会导致安装新模块。

## SEE ALSO 亦可参阅

* [npm-ls(1)](https://docs.npmjs.com/cli/ls)
* [npm-update(1)](https://docs.npmjs.com/cli/update)
* [npm-install(1)](https://docs.npmjs.com/cli/install)
