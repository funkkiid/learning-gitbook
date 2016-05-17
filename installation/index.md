gitbook安装
===========


# Linux 安装

## 安装node.js

### 手工安装

下载地址: https://nodejs.org/en/

将下载下来的 node-v6.1.0-linux-x64.tar.xz 文件解压缩，然后将文件复制到 /user/share 目录下：

	sudo mv node-v6.1.0-linux-x64 /usr/share/nodejs
    sudo ln -s /usr/share/nodejs/bin/node /usr/local/bin/node
    sudo ln -s /usr/share/nodejs/bin/npm /usr/local/bin/npm

### 自动安装

可以用apt-get(或者yum)自动安装，为了安装最新版本，需要增加nodejs的仓库：

    add-apt-repository ppa:chris-lea/node.js
    apt-get update
    apt-get install nodejs

完成之后执行version命令检验是否安装成功：

	npm --version

## 安装gitbook

	npm install -g gitbook gitbook-cli

## 初始化依赖

npm install .





