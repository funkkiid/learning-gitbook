# 提交文件到git仓库

## 设置git ignore文件

提交文件到git仓库时，注意一定要设置好.gitignore文件，推荐内容如下:

    .*
    !.gitignore
    _book
    node_modules

如果使用plantuml插件（后面会介绍)，则需要额外加入下面两行：

    assets/images/uml/*/*.uml
    assets/images/uml/*/*.uml.sum

## gitbook的规则

gitbook处理文件的规则是这样：

1. 处理范围： 根目录下的所有文件和文件夹，但是不包括 .gitignore 中要求ignore的文件
2. 转换方式： markdown文件(`*.md`)转为html文件，其他文件不转换
3. 生成路径： 所有文件(md文件指生成的HTML文件)和目录简单复制到 `_book` 目录，所有文件的路径维持不变


