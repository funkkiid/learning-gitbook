# 使用Jenkins自动发布

介绍使用 jenkins 来自动监控git仓库更新并生成HTML内容，再自动发布到nginx/apache等web服务器。

## 背景

github和gitbook都对书籍的发布提供了自动化的支持，比如github中可以方便的将生成的html page发布github pages上，gitbook更是天然支持。

但是对于一些不适合发布到github和gitbook的内容，比如公司内部的一些文档或者知识分享，就需要考虑其他的方式。

## 具体做法

### 准备jenkins和nginx

Jenkins/nginx的安装部署不在本书之列，我们假设jenkins/nginx服务器已经准备OK，而且在同一台物理机器上。

> 为什么要在同一台机器呢？
>
> 因为后面发布时涉及到文件复制，gitbook生成的文件终究是部署到nginx下的。如果是本地，就可以简单的通过shell命令复制文件，而如果不是本机，就需要其他的远程操作方式（比如scp），要复杂的多。
>
> 所以简单起见，在nginx所在的机器上安装一个文档自动发布的专用jenkins。

### 准备目录和权限

默认情况下jenkins执行脚本的用户名是 jenkins，为了让它可以有权限操作文件系统，需要修改目录权限。

假设我们需要将文档都放置到nginx下的docs目录，则需要提前准备这个目录：

	mkdir /usr/share/nginx/html/docs/
    chown jenkins:jenkins /usr/share/nginx/html/docs/

### 安装nodejs和gitbook

为了让jenkins可以执行 gitbook 的 build 命令，需要在jenkins所在机器上安装nodejs和gitbook，方法如前所述。

### 准备shell脚本

准备下面的bash脚本，保存为jenkins.sh，存放在git仓库的根目录下：

	#!/bin/bash

    source /etc/profile

    echo "**** env to build ****"
    echo `pwd`
    echo `id`
    echo "PATH=$PATH"

    echo "**** get content from git ****"
    echo `ls -l`
    echo

    echo "**** prepare nodejs ****"
    npm install
    echo "**** begin to build html ****"
    gitbook build
    echo "**** finish to build html ****"
    echo "static html content is located in _book folder:"
    echo `ls -l _book`

    echo "**** remove exist document ****"
    rm -rf /usr/share/nginx/html/docs/reference

    echo "**** copy content in _book to nginx ****"
    cp -r _book /usr/share/nginx/html/docs/reference

    echo "**** Done! ****"

    echo "new content is published to nginx:"
    echo `ls -l /usr/share/nginx/html/docs/reference`

### 创建jenkins的Job

在这个jenkins的Job中，设置 `Poll SCM: H/2 * * * *` 来每3分钟检查一次git，然后执行command `sh jenkins.sh`。

## 总结

这样就实现了 jenkins 自动监控git仓库，发现更新就执行bash脚本，生成HTML内容，再自动复制文件到nginx服务器。做法不复杂，但是完成之后，后续的文档更新就简单了，只需要简单提交内容到git仓库，一些简单的修改甚至直接在gitlab的web界面上就可以完成。


