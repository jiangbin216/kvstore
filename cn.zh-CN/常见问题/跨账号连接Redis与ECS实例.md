# 跨账号连接Redis与ECS实例 {#concept_q2p_flf_2gb .concept}

您可以使用阿里云的云企业网或者高速通道服务使不同阿里云账号下的VPC得以互通，从而实现两个账号下Redis和ECS的内网连接。

## 使用云企业网连接 {#section_tqd_dnf_2gb .section}

云企业网（Cloud Enterprise Network）帮助您在VPC间，VPC与本地数据中心间搭建私网通信通道，通过自动路由分发及学习，提高网络的快速收敛和跨网络通信的质量和安全性，实现全网资源的互通，帮助您打造一张具有企业级规模和通信能力的互联网络。您可以通过组建云企业网的方式连接不同账号下的资源。

**说明：** 

-   如果不需要跨地域部署，且没有账号限制，阿里云建议您将ECS实例与Redis实例创建在同一账号下、同一地域的同一VPC中。
-   在条件允许的情况下，推荐您将不同账号下的ECS与Redis实例迁移到同一账号下。以下文档可能为您提供更多帮助：
    -   [跨账号迁移Redis实例中的数据](../../../../cn.zh-CN/用户指南/数据迁移/云数据库Redis版之间迁移/使用redis-shake在云数据库Redis版实例之间迁移.md#)；
    -   [使用全球多活进行跨地域实例迁移](../../../../cn.zh-CN/用户指南/数据迁移/云数据库Redis版之间迁移/使用全球多活进行跨地域实例迁移.md#)。

**操作步骤**

1.  根据实际环境，选择通过云企业网进行内网互通的方式并按照指引操作：
    -   [跨账号同地域互通](https://help.aliyun.com/document_detail/65901.html)；
    -   [跨账号跨地域互通](https://help.aliyun.com/document_detail/65936.html)。
2.  在ECS的安全组入方向和出方向规则中允许ECS与Redis的连接。

    **说明：** 您可以在ECS中使用`ping <host>`命令（host为Redis实例的连接地址）查看Redis的内网IP地址，并将其设置在安全组规则中。ECS安全组规则配置方法请参见[ECS产品文档](https://help.aliyun.com/document_detail/58309.html)。

3.  在Redis的白名单中[加入ECS实例的内网IP](../../../../cn.zh-CN/用户指南/实例管理/设置IP白名单.md#)。
4.  在ECS中使用`ping <host>`命令确认连接成功，示例如下。

    ![ping测试示例](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80706/156385284238517_zh-CN.png)

    **说明：** 

    -   首次连接如果出现问题请先检查云企业网配置，如果配置无误但依然无法连接，您可以提交工单排查云企业网的连接问题。
    -   如果之前已经连接上，在业务运行过程中出现突发的连接问题，请参见[Redis连接问题排查与解决](cn.zh-CN/常见问题/Redis连接问题排查与解决.md#)进行排查。

## 使用高速通道连接 {#section_xqc_hpf_2gb .section}

阿里云高速通道（Express Connect）帮助您在专有网络（VPC）与本地数据中心之间、VPC与VPC间建立私网通信通道，提高网络拓扑的灵活性和跨网络通信的质量和安全性。高速通道可以避免网络质量不稳定问题，同时可以免去数据在传输过程中被窃取的风险。您可以使用高速通道在不同账号的VPC网络之间建立内网连接。

**操作步骤**

1.  在两个账号的VPC之间[创建高速通道连接](https://help.aliyun.com/document_detail/44842.html)。
2.  在ECS的安全组入方向和出方向规则中允许ECS与Redis的连接。

    **说明：** 您可以在ECS中使用`ping <host>`命令（host为Redis实例的连接地址）查看Redis的内网IP地址，并将其设置在安全组规则中。ECS安全组规则配置方法请参见[ECS产品文档](https://help.aliyun.com/document_detail/58309.html)。

3.  在Redis的白名单中[加入ECS实例的内网IP](../../../../cn.zh-CN/用户指南/实例管理/设置IP白名单.md#)。
4.  在ECS中使用`ping <host>`命令确认连接成功，示例如下。

    ![ping测试示例](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80706/156385284238517_zh-CN.png)

    **说明：** 

    -   首次连接如果出现问题请先检查高速通道配置，如果配置无误但依然无法连接，您可以提交工单排查高速通道的连接问题。
    -   如果之前已经连接上，在业务运行过程中出现突发的连接问题，请参见[Redis连接问题排查与解决](cn.zh-CN/常见问题/Redis连接问题排查与解决.md#)进行排查。

