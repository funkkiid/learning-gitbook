# Node.js 安装

gitbook是基于node.js的，因此必须先安装 nodejs 的 runtime 才可以使用。

请先安装完nodejs之后，再继续后面的安装。

## Windows下安装node.js

https://nodejs.org/en/download/ 下载 Windows Installer (.msi) 的 64位版本，一般用LTS版本即可。

## Linux下安装node.js

下载地址: https://nodejs.org/en/

将下载下来的 node-v6.1.0-linux-x64.tar.xz 文件解压缩，然后将文件复制到 /user/share 目录下：

```bash
sudo mv node-v6.1.0-linux-x64 /usr/share/nodejs
```

打开 /etc/profile, 添加下来内容,将 `/usr/share/nodejs/bin` 加入PATH 路径:

```bash
export PATH=/usr/share/nodejs/bin:$PATH
```

完成之后执行version命令检验是否安装成功：

```bash
source /etc/profile
npm --version
```

注意这里一定要将 `/usr/share/nodejs/bin` 加入到 PATH，不然后面安装其他内容后使用时会报错找不到命令，因为通常新安装的命令都会放在 `/usr/share/nodejs/bin`：

```bash
gitbook serve
You need to install "gitbook-cli" to have access to the gitbook command anywhere on your system.
If you've installed this package globally, you need to uninstall it.
>> Run "npm uninstall -g gitbook" then "npm install -g gitbook-cli"
```

## 指定nodejs的仓库

默认安装之后，nodejs使用的时官方的默认仓库 `https://registry.npmjs.org/`，这样不仅仅下载速度慢，而且有时会出现校验和报错：

```bash
npm ERR! shasum check failed for /tmp/npm-7141-389856ed/registry.npmjs.org/gitbook/-/gitbook-3.2.2.tgz
npm ERR! Expected: 2b5157d358777a95f916499f385d859ccea0bf25
npm ERR! Actual:   64ee40094cb0b061f3d16fe3c4d9d2c235b4df94
npm ERR! From:     https://registry.npmjs.org/gitbook/-/gitbook-3.2.2.tgz
```

解决的方式时指定nodejs的仓库为国内仓库，如国内最大的nodejs社区 `http://cnodejs.org` 提供的仓库。方法有三种：

1. 通过config命令

    ```bash
    npm config set registry http://registry.cnpmjs.org
    npm info underscore （如果上面配置正确这个命令会有字符串response）
    ```

2. 在npm命令行指定

    ```bash
    npm --registry http://registry.cnpmjs.org info underscore
    ```

3. 修改 ~/.npmrc

	编辑这个文件，如果没有则添加，加入内容：

    ```bash
    registry = http://registry.cnpmjs.org
    ```

以上任意一种都能解决问题，建议第三种，不用每次都设置。
