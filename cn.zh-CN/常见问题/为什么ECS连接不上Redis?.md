# 为什么ECS连接不上Redis? {#concept_m2x_pbz_xdb .concept}

两者通过内网连接必须满足的条件如下：

-   ECS和Redis在相同的地域

-   ECS和Redis在相同的网络环境，即：必须都属于经典网络或者同一个VPC下

-   ECS内网IP在Redis白名单中


以下情况中，ECS无法直接通过内网连接Redis数据库。

-   如果您的ECS和redis在不同地域的VPC中，内网是不通的。在不同地域下的ECS连接Redis，目前只能通过高速通道实现跨VPC的内网访问，详情参见 [跨地域VPC互连](https://help.aliyun.com/document_detail/44842.html)。

-   如果您的ECS和redis属于不同的网络类型，您可以通过如下方法来解决：

    -   如果可以接受转换为VPC网络类型，请参考[切换为专有网络](../../../../../cn.zh-CN/用户指南/管理实例/切换为专有网络.md#)或者[迁移方案概述](https://help.aliyun.com/document_detail/55051.html)。

    -   如果不接受转化为VPC，您需要重新购买同一地域下、同属经典网络的ECS和Redis。


您还可以参见[连接问题排查与解决](cn.zh-CN/常见问题/Redis连接问题排查与解决.md#)查看更多相关信息。

