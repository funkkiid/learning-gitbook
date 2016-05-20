jenkins自动发布
=============

# 安装jenkins



centos：

	wget -O /etc/yum.repos.d/jenkins.repo http://jenkins-ci.org/redhat/jenkins.repo
	rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
	yum install jenkins

启动jenkins：

service jenkins start

jenkins执行 `gitbook build` 命令时报错:

>gitbook: command not found

检查发现jenkins在运行时是以用户 `jenkins` 执行任务, /etc/profile 中的PATH设置没有生效, `/usr/share/nodejs/bin` 没有加入PATH路径.

因此需要增加几个软链接避开这个问题:

    ln -s /usr/share/nodejs/bin/node /usr/local/bin/node
    ln -s /usr/share/nodejs/bin/npm /usr/local/bin/npm
    ln -s /usr/share/nodejs/bin/gitbook /usr/local/bin/gitbook
    ln -s /usr/share/nodejs/bin/grunt /usr/local/bin/grunt

执行 `cat /etc/passwd` 命令,发现安装jenkins时自动增加的jenkins用户默认是不然登录的:

	jenkins:x:497:498:Jenkins Continuous Integration Server:/var/lib/jenkins:/bin/false

为了方便调试 bash 脚本, 修改为容许登录:

	usermod -s /bin/bash jenkins