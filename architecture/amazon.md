Amazon架构分享
---------------------

Amazon分布式缓存架构图：
![缓存架构图](https://hotbain.gitbooks.io/e-commerce-java-development-technology/content/image/amazon.jpg)

Dynamo是亚马逊的key-value模式的存储平台，可用性和扩展性都很好，性能也不错：读写访问中99.9%的响应时间都在300ms内。按分布式系统常用的哈希算法切分数据，分放在不同的node上。Read操作时，也是根据key的哈希值寻找对应的node。Dynamo使用了 Consistent Hashing算法，node对应的不再是一个确定的hash值，而是一个hash值范围，key的hash值落在这个范围内，则顺时针沿ring找，碰到的第一个node即为所需。

Dynamo对Consistent Hashing算法的改进在于：它放在环上作为一个node的是一组机器（而不是memcached把一台机器作为node），这一组机器是通过同步机制保证数据一致的。

这种缓存机制是我我自己最喜欢的一种方式，因为这样添加缓存节点的都是添加到一个节点组中，同一组里的节点都是对等的，便于扩展和高可用保证.

分布式存储系统的示意图
------------------------

![搜索架构图](https://hotbain.gitbooks.io/e-commerce-java-development-technology/content/image/amazon_cache.jpg)


Amazon云架构图
-------------------------
![amazon云架构图](https://hotbain.gitbooks.io/e-commerce-java-development-technology/content/image/amazon_cloud.png)

鄙人有些地方稍微有些看不懂这种图。大家自己看一张图吧!!!