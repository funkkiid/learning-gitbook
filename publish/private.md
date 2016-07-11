# 私有方案

私有方案是指采用私有git仓库存储书籍内容 + 使用私有web服务器发布HTML内容。

适合用于私有环境，比如公司内部。

## 内容存储

通常推荐搭建gitlab来管理git仓库，然后新建仓库来存放一些以gitbook格式存放的开发文档。

具体git/gitlab的使用不在本书范围。

## 发布

发布的方式也足够简单，一个 `gitbook build` 命令搞定：

    gitbook build
    info: loading book configuration....OK
    info: load plugin gitbook-plugin-highlight ....OK
    info: load plugin gitbook-plugin-search ....OK
    info: load plugin gitbook-plugin-sharing ....OK
    info: load plugin gitbook-plugin-fontsettings ....OK
    info: >> 4 plugins loaded
    info: start generation with website generator
    info: clean website generator
    info: OK
    info: generation is finished

    Done, without error

之后简单将 `_book` 目录下的文件复制到 apache/nginx 下发布即可。

## 总结

使用足够简单，唯一的麻烦是需要自己build并发布。

下一节将介绍使用 jenkins 来自动监控git仓库更新并生成HTML内容，再自动部署到nginx/apache等web服务器。
