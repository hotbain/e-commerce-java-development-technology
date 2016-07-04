Java程序员眼中的电商网站
=======

大家好，我是一名Java程序员，从14年开始就开始从事电商网站的开发，做了也有一点时间了，虽然自己工作的时间不长，但是感觉做电商项目让自己学习到的东西相对于别的项目类型来说，多很多。处于和大家分享的目的， 我想写一本关于从Java开发的角度看电商项目开发的技术书籍，我是一个developer，当然是从技术的角度去讲，力求简单明了，提纲挈领.当然了，大家也可以在阅览时，随时gitbook上对我的文章内容进行评价(GitBook提供了这个功能)，我也会积极的对其中的评论进行回复。

梦想
-------
每一个人都有一个梦想，我的梦想是写一本书，这本书涉及到我的生活或者技术，这要是我自己想写入的内容，都可以写到这本书里。我想这本书可能就是吧。偶然的机会，我认识了GitBook，我看到了希望，不用再去想象着书籍的编写路上的艰辛(出版社等嘈杂的事务)。


技术
----------------------------------------

电商项目涉及到用户金额，所以对技术的要求非常严苛。因为稍微控制不好，就会出现金额丢失等严重问题。当数据访问量大时，这种问题发生的概率更大。怎样控制好访问量，都是我们在进行系统设计和开发时应该注意的问题。

1. 用户访问网站，获得html页面，通过cdn加载最近的静态资源，
1. 然后页面是模块化的，都是异步加载的，根据用户的浏览习惯，投其所好，进行加载。
1. 加载完成后，进行商品的搜索，就会涉及到搜索引擎，怎么提高匹配度，搜到自己想要的商品后，
1. 进入商品详情页，商品详情页会包含自己的浏览历史，以及商品详情(这些商品详情都是从静态，是静态化了的。)，已经商品详情，商品静态文件存储在怎样的文件系统里(静态文件特别小，量特别大，不是所有的文件系统都可以处理。)
1. 浏览的过程中，还会通过js异步加载商品的评论，这些评论后台存储是怎样的。
1. 浏览完毕后，将需要加入到购物车，购物车后台用什么样的系统进行存储。
1. 订单提交过程，怎样避免重复提交?
1. 订单量大时，怎样快速处理订单系统的异步回调？
2. 秒杀怎样实现？
3. 活动或者节日，怎样进行业务降级，保证主要流程？

上面这些技术都是我们在实现电商系统时会遇到的问题中的几个，还有很多问题需要去解决。上面的问题都是我要在本书里进行阐述的，每个人的能力是有限的，但是每个人对外面的世界都是感兴趣的。了解不一定就是一个方面的专家.

起航
----------------------------------------


12/26/2015 7:51:14 PM 


