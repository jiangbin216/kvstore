# 跨账号连接Redis与ECS实例 {#concept_q2p_flf_2gb .concept}

您可以使用阿里云的云企业网或者高速通道服务使不同阿里云账号下的VPC得以互通，从而实现两个账号下Redis和ECS的内网连接。

## 使用云企业网连接 {#section_tqd_dnf_2gb .section}

云企业网（Cloud Enterprise Network）帮助您在VPC间，VPC与本地数据中心间搭建私网通信通道，通过自动路由分发及学习，提高网络的快速收敛和跨网络通信的质量和安全性，实现全网资源的互通，帮助您打造一张具有企业级规模和通信能力的互联网络。您可以通过组建云企业网的方式连接不同账号下的资源。

**操作步骤**

1.  根据实际环境，选择通过云企业网进行内网互通的方式并按照指引操作：
    -   [跨账号同地域互通](https://help.aliyun.com/document_detail/65901.html)；
    -   [跨账号跨地域互通](https://help.aliyun.com/document_detail/65936.html)。
2.  在 ECS 的安全组中[配置相应的授权规则](https://help.aliyun.com/document_detail/25471)，允许其访问 Redis。
3.  在 Redis 的白名单中[加入ECS实例的内网IP](../../../../../cn.zh-CN/用户指南/管理实例/设置IP白名单.md#)。
4.  在ECS中使用ping <host\>命令测试连通状况。

    **说明：** host为Redis的连接地址。


## 使用高速通道连接 {#section_xqc_hpf_2gb .section}

阿里云高速通道（Express Connect）帮助您在专有网络（VPC）与本地数据中心之间、VPC与VPC间建立私网通信通道，提高网络拓扑的灵活性和跨网络通信的质量和安全性。高速通道可以避免网络质量不稳定问题，同时可以免去数据在传输过程中被窃取的风险。您可以使用高速通道在不同账号的VPC网络之间建立内网连接。

**操作步骤**

1.  在两个账号的VPC之间[创建高速通道连接](https://help.aliyun.com/document_detail/44842.html)。
2.  在ECS的安全组中[配置相应的授权规则](https://help.aliyun.com/document_detail/25471)，允许其访问 Redis。
3.  在Redis的白名单中[加入ECS实例的内网IP](../../../../../cn.zh-CN/用户指南/管理实例/设置IP白名单.md#)。
4.  在ECS中使用ping <host\>命令测试连通状况。

    **说明：** host为Redis的连接地址。


## 最佳实践 { .section}

如果不需要跨地域部署，且没有账号限制，阿里云建议您将ECS实例与Redis实例创建在同一账号下，同一地域的同一VPC中。

在条件允许的情况下，推荐您将不同账号下的ECS与Redis实例迁移到同一账号下。以下文档可能为您提供更多帮助：

-   [跨账号迁移Redis实例中的数据](../../../../../cn.zh-CN/用户指南/迁移数据/云数据库Redis版之间迁移/使用redis-port跨账号迁移.md#)；
-   [使用全球多活进行跨地域实例迁移](../../../../../cn.zh-CN/用户指南/迁移数据/云数据库Redis版之间迁移/使用全球多活进行跨地域实例迁移.md#)。

