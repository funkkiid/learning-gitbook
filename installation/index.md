gitbook安装
===========

## 概述

安装使用 gitbook 需要以下步骤:

1. 安装node.js 运行时
2. 安装gitbook

然后根据需要可以选择以下内容：

* 安装grunt： 方便将生成的静态内容发布到 github

## 安装node.js

gitbook是基于node.js的，因此必须先安装nodejs的runtime才可以使用。

请先安装完nodejs之后，再继续后面的安装。

### Windows下安装node.js

https://nodejs.org/en/download/ 下载 Windows Installer (.msi) 的 64位版本，一般用LTS版本即可。

### Linux下安装node.js

#### 手工安装

下载地址: https://nodejs.org/en/

将下载下来的 node-v6.1.0-linux-x64.tar.xz 文件解压缩，然后将文件复制到 /user/share 目录下：

	sudo mv node-v6.1.0-linux-x64 /usr/share/nodejs

打开 /etc/profile, 添加下来内容,将 `/usr/share/nodejs/bin` 加入PATH 路径:

	export PATH=/usr/share/nodejs/bin:$PATH

完成之后执行version命令检验是否安装成功：

	source /etc/profile
	npm --version

#### 自动安装

可以用apt-get(或者yum)自动安装，为了安装最新版本，需要增加nodejs的仓库：

    add-apt-repository ppa:chris-lea/node.js
    apt-get update
    apt-get install nodejs

安装完成之后，可以执行命令查看当前版本：

	npm --version

### 搭建nodejs私库

对于公司内部使用，最好搭建一个nodejs的私库，避免每个人都去下载耗时太多。

> 注： 参考文章 [5 分钟搭建一个私有 npm registry]( https://github.com/cnpm/cnpmjs.org/wiki/Deploy-a-private-npm-registry-in-5-minutes)
>
> 注2：还没有测试过

### 安装gitbook

通过下列命令安装 gitbook 和 gitbook-cli

	npm install -g gitbook gitbook-cli

安装完成之后，执行 `gitbook --version` 命令可以看到当前安装的版本：

    2.1.3

### 安装grunt

> 注：只有需要将内容发布到github pages时才需要grunt

通过下列命令安装 grunt 和 grunt-cli

	npm install -g grunt grunt-cli

安装完成之后，执行 `grunt --version` 命令可以看到当前安装的版本：

    grunt-cli v0.1.13
    grunt v0.4.5


