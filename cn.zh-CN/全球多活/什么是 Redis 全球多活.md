# 什么是 Redis 全球多活 {#concept_qf1_mdk_zdb .concept}

**Redis 全球多活**是阿里自研的、基于云数据库 Redis 版（ApsaraDB for Redis）、100%兼容 Redis 协议的多活数据库系统。通过数据同步通道，把多个 Redis 子实例组网成1个逻辑上的多活实例，所有子实例均可读写并保持实时数据同步。

**Redis 全球多活**轻松支持异地多个站点同时对外提供服务的业务场景，助力企业快速复制阿里巴巴异地多活架构。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/14010/15411302079906_zh-CN.png)

