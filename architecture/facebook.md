Facebook搜索架构
-----------------

![搜索架构图](https://hotbain.gitbooks.io/e-commerce-java-development-technology/content/image/facebook_search_arthciture.png)

---------------
1. 前端搜索服务通过Thrift来访问搜索服务
1. 后台会有个建立索引服务从数据库或者log文件将其索引到后台的slave中，当需要将索引上线时，将slave index当成master index使用即可。然后拷贝出一份slave index继续与后台的索引服务进行同步.


-------------------------------

其实现在市面上也有很多的开源搜索中间件，例如solr/ElasticSearch.做一个集群和搜索结果缓存也能够很好的满足自己的业务需求，电商项目里也是经常用到.
