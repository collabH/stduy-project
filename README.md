这个是我学习时，写的一个基于SOA的架构的电商项目，主要基于SSM框架，也用到了Springboot开发短信微服务模块，后期也通过伪分布式来搭建nginx集群，zookeeper集群，以及mysql和redis等的一些集群。

环境:SpringBoot+Soa+SpringMVC + Spring + Mybatis + angluarjs+ Maven + MySQL+Tomcat+nginx+SpringSecurity+SpringDataSolr+SpringDataRedis+
SpringTask+Freemarker

项目介绍：
SOA架构的网上商城是一个综合性的 B2B2C 平台，类似京东商城、天猫商城。网站采用商家入驻的模式，商家入驻平台提交申请，有平台进行资质审核，审核通过后，商家拥有独立的管理后台录入商品信息。商品经过平台审核后即可发布。
SOA架构的网上商城主要分为网站前台、运营商后台、商家管理后台三个子系统

工作描述：
1、  网站前台相关功能(主要包括网站首页、商家首页、商品详细页、搜索页、会员中心、订单与支付相关页面、秒杀频道等)
2、  运营商后台相关功能( 运营商后台是运营商的运营人员的管理后台。 主要包括商家审核、品牌管理、规格管理、模板管理、商品分类管理、商品审核、广告类型管理、广告管理、订单查询、商家结算等)
3、   商家管理后台相关功能(入驻的商家进行管理的后台，主要功能是对商品的管理以及订单查询统计、资金结算等功能)；

技术描述
1、使用SpringSecurity负责本网站信息的认证和安全的控制。
2、本系统基于SOA架构开发,将各个模块拆分开。
3、使用SpringBoot结合阿里大于开发短信微服务。
4、Angluarjs前端技术将前端进行MVC架构分离,解耦合。
5、购物车系统是使用Cookie和Redis进行存取(没有登录使用Cookie登录后使用     redis存储，在将cookie中的购物车对象信息合并到redis中)
6、使用微信扫码SDK接口,生成一个url通过qrious二维码生成技术生成二维码。
7、项目之间各服务的通信使用dubbox分布式框架,zookeeper作为注册中心对服务的消费者和生产者进行调度。
8、考虑到商品详情页面并发量高，使用freemarker静态页面技术,将该页面生成静态页面在硬盘上,在将这些页面部署到nginx服务器上,通过url访问即可。
9、使用Solr全文检索技术，通过SpringDataSolr实现商品搜索。
10、首页导航信息使用redis缓存，大大提高了页面的刷新效率,减少对数据库的访问压力
11、后期部署:zookeeper集群(实现service各个服务间的负载均衡)、redis集群、解决海量数据解决方案(mycat分片技术 使用分片规则为:哈希一致性)、nginx负载均衡(实现各个web应用服务器的负载均衡)、nginx反向代理解决高并发问题。
