# 私有方案

采用私有git仓库存储 + 私有web服务器发布

这种方式适合用于私有环境，比如公司内部(当然如果购买了github和gitbook的收费服务不在此列)。

搭建一个gitlab，存放一些以gitbook格式存放的开发文档，然后通过ci服务器（如jenkins）监控更新并生成HTML内容，再部署到nginx/apache等web服务器。