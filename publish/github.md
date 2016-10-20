# github方案

tags: github

github方案是指采用github提供的git仓库存储书籍内容，并使用github pages服务发布HTML内容。

适合用于公共环境，比如存放一些公开信息(如我喜欢的各种学习笔记)。

## 内容存储

github提供的git仓库,简单新建仓库，然后提交书籍内容即可。

## 发布

将gitbook生成的html page发布github pages上(实际是提交内容到gh-pages 分支)，如果没有工具，会非常的麻烦。

好在 grunt (算是这个nodejs世界下的maven?)提供了支持，可以方便的实现我们需要的功能。

## 具体做法

### 安装grunt

简单通过 npm 命令可以安装：

	npm install -g grunt grunt-cli

完成之后检查一下：

    $ grunt --version
    grunt-cli v0.1.13

### 准备package.json和Gruntfile.js文件

package.json 文件用来配置 nodejs 的依赖(类似maven中的pom.xml里面的<dependencies/>段), 参考内容如下，自行修改即可：

[package.json](images/package.json)

> 注意： name 不能带有空格，否则npm install的时候会报错。

Gruntfile.js 文件是 grunt 的配置文件和脚本，参考内容如下：

[Gruntfile.js](images/Gruntfile.js)

下面是 Gruntfile.js 中最重要的内容，git仓库的信息一定要正确填写：

    "repository": {
        "type": "git",
        "url": "https://github.com/skyao/leanging-gitbook"
    },

### 安装依赖

执行命令 `npm install .`， 将根据 package.json 中配置的依赖信息将相关的依赖下载到 node_modules 目录。

### 本地测试

grunt 安装好之后，在本机编辑书籍内容时，可以用 grunt 启动服务器：

	grunt test

这个方法类似 `gibook serve` (实际里面也调用了gitbook的命令)，之后打开浏览器(grunt脚本中有自动打开浏览器的设置)访问即可.日志如下：

    $ grunt test
    Running "gitbook:development" (gitbook) task

    Running "http-server:dev" (http-server) task
    Server running on http://0.0.0.0:4000/
    Hit CTRL-C to stop the server

    Running "open:all" (open) task

    Running "watch" task
    Waiting...

### 发布到github pages

终于到最后一步了，我们的目标是要将build 出来的内容(_book目录下)发布到github，存放在gh-pages分支。此时需要的只是一个简单命令：

	grunt publish

可以看到如下的日志：

    Running "gitbook:development" (gitbook) task

    Running "gh-pages:src" (gh-pages) task
    Cloning git@github.com:skyao/leaning-gitbook.git into .grunt/grunt-gh-pages/gh-pages/src
    Cleaning
    Fetching origin
    Checking out origin/gh-pages
    Removing files
    Copying files
    Adding all
    Committing
    Pushing

    Running "clean:files" (clean) task
    >> 1 path cleaned.

    Done, without errors.

### 浏览发布内容

从浏览器中直接访问就可以看到发布的结果：

http://skyao.github.io/leaning-gitbook/

注意这里路径的对应：

1. 假如git仓库是地址 https://github.com/skyao/leanging-gitbook,格式是 "github.com/$account/$repo"
2. 则github pages的URL是 http://skyao.github.io/leaning-gitbook/，格式是 "$account.github.io/$repo"，注意域名从github.com变成了github.io

## 总结

在使用 grunt 之后，发布到github pages就方便多了。

