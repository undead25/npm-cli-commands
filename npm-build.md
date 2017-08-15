npm-build(1) -- 构建一个包
===============================

## SYNOPSIS 概要
```
npm build [<package-folder>]
```

* `<package-folder>`:
  在其根目录中包含一个 `package.json` 文件的文件夹。


## DESCRIPTION 描述
这是由 `npm link` 和 `npm install` 调用的管道命令。

它通常在安装过程中被调用，但是如果你需要直接运行它，请运行：

```bash
npm run-script build
```

## SEE ALSO 亦可参阅
* [npm-install(1)](https://docs.npmjs.com/cli/install)
* [npm-link(1)](https://docs.npmjs.com/cli/link)
* [npm-scripts(7)](https://docs.npmjs.com/misc/scripts)
* [package.json(5)](https://docs.npmjs.com/files/package.json)
