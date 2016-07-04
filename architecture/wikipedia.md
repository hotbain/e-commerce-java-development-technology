维基百科架构
-------------


直接上图：
![模型编辑](https://hotbain.gitbooks.io/e-commerce-java-development-technology/content/image/wikipedia.png)
-------------------

1. 首先通过LVS进行负载均衡
1. 然后会访问通过Squid设置的图片缓存
1. 然后再次进入LVS对后台应用服务器做的负载均衡集群
1. 在服务器中还要使用到lucene搜索引擎、Memcache分布式对象缓存、Mysql数据库集群、以及其他外部存储设备.



整体看一下它的架构，还是比较简单，就是做了均衡，和缓存设置。当然我想这其中肯定会涉及到其他例如CDN以及服务集群化的一些优化措施，毕竟维基百科。

如果电商项目，那么还会多出很多组件，例如监控组件，搜索组件(elasticsearch/solr)，消息组件(kafka/activeMq),数据库集群(Cobar/Mycat),分布式文件系统(TFS/Hdfs)组件。

不同的场景具有不同的架构设计，维基百科的大部分请求都是对一些静态文件，热门词条，文档内容的请求，这些内容就可以通过反向代理集群的方式将压力挡在了应用服务器的外面，让服务器的压力骤减.如果词条有更新的话，那么就会通知Squid缓存失效，进行重新访问。其实缓存也是分级别的，有些特别热门的数据也是缓存到本地内容的，因为要占用应用服务器的内存，所以数据量特别小，但是访问量会特别大，命中率也会很高。并且缓存的内容也是可以直接被应用服务器直接使用的格式，例如html文本，这样减小解析的压力。使用缓存服务器存储session对象（电商项目可以考虑使用taobao的tair缓存.）在数据库方面，如果master数据库宕机，立即将应用切换到slave数据库，同事关闭数据的写服务，这意味着关闭词条编辑功能。维基百科通过约束业务获得更大的技术方案选择余地，其实在业务上退后一步，技术上就可以前进一大步。在电商里面，我们可以通过业务降级，在特定的时刻，将一些不主要的业务关掉，也是一种义务上的让步.例如在活动期间，关闭订单评价，商品评价，退款功能，部分订单列表查看功能，这些都是可以进行控制，最好是在设计产品的时候，就要将这种问题考虑进去，这样是会对技术的扩展有利的。