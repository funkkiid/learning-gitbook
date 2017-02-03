# Gitbook安装

## 安装Gitbook

通过下列命令安装 gitbook 和 gitbook-cli

```bash
npm install -g gitbook gitbook-cli
```

切记在执行这个安装命令前，有：

1. 设置nodejs的仓库
2. 在linux下，请将 `/usr/share/nodejs/bin` 加入PATH
3. 在windows下，请务必在windows的 cmd 命令行下执行上述`npm install` 命令，不要在linux shell下(比如安装git之后的shell)安装，否则执行gitbook 总是会报错:

	```bash
    You need to install "gitbook-cli" to have access to the gitbook command anywhere on your system.
	If you've installed this package globally, you need to uninstall it.
	>> Run "npm uninstall -g gitbook" then "npm install -g gitbook-cli"
    ```

安装完成之后，执行 `gitbook --version` 命令可以看到当前安装的版本：

```bash
$ gitbook --version
CLI version: 2.3.0
GitBook version: 3.2.2
```

## 安装grunt

> 注：只有需要将内容发布到github pages时才需要grunt

通过下列命令安装 grunt 和 grunt-cli

```bash
npm install -g grunt grunt-cli
```

安装完成之后，执行 `grunt --version` 命令可以看到当前安装的版本：

```bash
$ grunt --version
grunt-cli v1.2.0
```

## 初始化gitbook

进入任何一本 gitbook 的书籍，执行 `gitbook serve` 命令，第一次执行时会初始化 GitBook：

```bash
$ cd leaning-gitbook/
sky@skylinux ~/work/code/leaning/leaning-gitbook $ gitbook serve
Installing GitBook 3.2.2
gitbook@3.2.2 ../../../../../../tmp/tmp-109965s9a5ZM8Xffp/node_modules/gitbook
├── escape-html@1.0.3
├── escape-string-regexp@1.0.5
├── destroy@1.0.4
......
└── npm@3.9.2
Live reload server started on port: 35729
Press CTRL+C to quit ...

info: 7 plugins are installed
info: loading plugin "livereload"... OK
info: loading plugin "highlight"... OK
......
Starting server ...
Serving book on http://localhost:4000
```

这个初始化工作只会做一次，之后再运行，哪怕是在其他书籍目录下执行，也不需要再初始化。

