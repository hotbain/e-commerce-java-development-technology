购物车设计与实现
-----------------

购物车就是用来暂存我们想购买的商品，然后一次性提交，进行结算。我们会通过以下几个维度来评判购物车存储的好坏。大家可以根据自己的业务需求来选择合适的存储方式.


> 1. 是否能够在不同的客户端共享购物车信息
> 1. 是否能够长期存储购物车信息
> 1. 存储成本以及技术实现成本 

下面我们讲一下购物车后台的存储方式。


----------

#####Cookie存储

不能够与其它客户端共享购物车信息；不能够长期存储；技术实现成本低

#####Session存储

不能够与其它客户端共享购物车信息(除非session共享)；不能够长期存储；技术实现成本比较低(Session信息过大的话，也会出现过载问题.)

#####DB存储

这里Db可以使Nosql或者RDBMS进行购物车信息的存储。很明显这种方式能够实现购物车共享；能够长期存储；技术实现成本低。

业界目前基本上都是使用的第三种方式来存储购物车信息。其实不同的电商项目业务类型也是不同的。例如 团购建议使用Cookie，因为团购基本上都是购买一件，然后直接下单，所以这个时候使用cookie是最好的一种方式。但是想淘宝/jd这种可以选多种不同商店的不同商品进行购买的情况，这个时候就比较适合DB存储。一个是购买的商品比较多，二是 可以在不同的共享购物车数据。用户登出后，购物车信息不会丢失，再次登录还会出现上次想购买的商品。

不同的购物车实现都是和业务场景相关的。对于使用DB存储实现的购物车，基本上都是使用mongodb做购物车的实现。mongoDb的schema都是动态创建，可以很好的用到购物车DB存储中。这样使用不同的客户端访问购物车就可以根据用户标识去mongo查询商品信息了，实现了购物车信息的共享.再就是购物车过期问题，其实主要是看自己的业务场景，如果需要一定的过期时间，那么就需要一个过期机制去保证这一点。

----------------------------------------------

备注：
后期我也会写一个mongo集群搭建的章节，供大家学习.