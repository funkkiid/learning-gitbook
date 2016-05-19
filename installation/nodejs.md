node.js安装配置
===========

# 安装node.js

## Linux下安装node.js

### 手工安装

下载地址: https://nodejs.org/en/

将下载下来的 node-v6.1.0-linux-x64.tar.xz 文件解压缩，然后将文件复制到 /user/share 目录下：

	sudo mv node-v6.1.0-linux-x64 /usr/share/nodejs

打开 /etc/profile, 添加下来内容,将 `/usr/share/nodejs/bin` 加入PATH 路径:

	export PATH=/usr/share/nodejs/bin:$PATH

完成之后执行version命令检验是否安装成功：

	npm --version

### 自动安装

可以用apt-get(或者yum)自动安装，为了安装最新版本，需要增加nodejs的仓库：

    add-apt-repository ppa:chris-lea/node.js
    apt-get update
    apt-get install nodejs

## Windows下安装node.js

https://nodejs.org/en/download/ 下载 Windows Installer (.msi) 的 64位版本，一般用LTS版本即可。

# 搭建nodejs私库

对于公司内部使用，最好搭建一个nodejs的私库，避免每个人都去下载耗时太多。

> 注： 参考文章 [5 分钟搭建一个私有 npm registry]( https://github.com/cnpm/cnpmjs.org/wiki/Deploy-a-private-npm-registry-in-5-minutes)







