# 为什么ECS连接不上Redis {#concept_m2x_pbz_xdb .concept}

如果您的ECS实例无法通过内网或者外网连接Redis实例，请根据本文的分类说明进行排查。

## 内网连接 {#section_s6y_yir_939 .section}

两者通过内网连接必须满足的条件如下：

-   ECS和Redis在相同的地域。
-   ECS和Redis在相同的网络环境，即：必须都属于经典网络或者同一个VPC下。
-   ECS内网IP在Redis白名单中。

以下情况中，ECS无法直接通过内网连接Redis数据库。

-   如果您的ECS和redis在不同地域的VPC中，内网是不通的。在不同地域下的ECS连接Redis，目前只能通过高速通道实现跨VPC的内网访问，详情参见 [跨地域VPC互连](https://help.aliyun.com/document_detail/44842.html)。
-   如果您的ECS和redis属于不同的网络类型，您可以通过如下方法来解决：
    -   如果可以接受转换为VPC网络类型，请参考[切换为专有网络](../../../../intl.zh-CN/用户指南/实例管理/切换为专有网络.md#)或者[迁移方案概述](https://help.aliyun.com/document_detail/55051.html)。
    -   如果不接受转化为VPC，您需要重新购买同一地域下、同属经典网络的ECS和Redis。

## 外网连接 {#section_hs9_qsw_a21 .section}

请按照[外网连接](../../../../intl.zh-CN/快速入门/步骤3：连接实例/外网连接.md#)的说明申请外网连接地址，使用该地址从因特网连接Redis实例。

您还可以参见[连接问题排查与解决](intl.zh-CN/常见问题/Redis连接问题排查与解决.md#)查看更多连接问题的排查方式。

