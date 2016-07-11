# plantuml插件

## plantuml介绍

plantuml是一个非常方便的uml工具，只要简单的编写文本，就可以得到对应的UML图形。

下面是plantuml的一些介绍资料和安装指导：

- [plantuml官网](http://plantuml.com//)
- [plantuml使用参考文档(PDF格式)](http://plantuml.com/PlantUML_Language_Reference_Guide.pdf)
- [plantuml安装配置](http://skyao.github.io/2014/12/05/plantuml-installation/)

## 集成到gitbook中

详细信息请见我之前的blog：

[配置使用gitbook的plantuml插件](http://skyao.github.io/2015/11/25/gitbook-plantuml-plugin/)

## 备注

使用过一段时间之后，发现用这个插件，生成UML是方便了，但是编辑plantuml内容时，在markdown编辑器中是无法实时看到UML图形的，非常的不方便。

只能先在其他plantuml工具中编辑完成，再将最终内容复制到markdown文件中。

后来干脆不用这个插件了，直接把plantuml的文件保存在images目录下，用工具编辑成功之后，再导出图片保存在和plantuml文件同一目录，文件名保持一致。以后修改内容时再重新生成图片覆盖就好了。

这个方案编辑速度不比用插件慢，而且省去了build的时候的麻烦。

以上行为仅仅是个人喜欢，仅供参考。