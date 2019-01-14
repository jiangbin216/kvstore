# 快速实现不同网络的ECS与Redis实例互访 {#concept_svr_jzt_zfb .concept}

如您的ECS实例在经典网络而 Redis 实例在专有网络（VPC），或Redis实例在经典网络而ECS实例在专有网络，可根据本文中的办法快速实现互通。

## 背景信息 {#section_i4r_wb5_zfb .section}

阿里云经典网络与专有网络（VPC）为不同的子网，无法直接互通，当环境中ECS与Redis实例处于不同网络类型中（例如创建实例时选择错误或者业务架构需要调整），并且业务场景需要尽快连通ECS和Redis时，可考虑切换Redis实例的网络类型或者使用ClassicLink实现互访。

**说明：** 基于ClassicLink互访方案为特殊情况下的临时解决方案，生产环境中为了实现高效缓存，阿里云建议您将ECS和Redis创建在同一VPC网络内。

## 经典网络ECS访问专有网络Redis {#section_vh5_rzt_zfb .section}

您可以通过建立ClassicLink连接，使经典网络的ECS实例和专有网络内的Redis实例互通。

**前提条件**

-   ECS与Redis实例在同一账号下且在同一地域。
-   专有网络中的网段设置需满足[开启ClassicLink的条件](https://help.aliyun.com/document_detail/65412.html)。

**说明：** 若ECS与Redis不在同一地域，为了快速使二者连通，可[使用全球多活进行跨地域实例迁移](../../../../../cn.zh-CN/用户指南/迁移数据/云数据库Redis版之间迁移/使用全球多活进行跨地域实例迁移.md#)，将Redis迁移到ECS所在地域。

**操作步骤**

1.  登录[云数据库Redis版管理控制台](https://kvstore.console.aliyun.com/)。
2.  将 ECS 实例的内网 IP [加入Redis实例白名单](../../../../../cn.zh-CN/用户指南/管理实例/设置IP白名单.md#)。
3.  [建立ClassicLink连接](https://help.aliyun.com/document_detail/65413.html)。
4.  在ECS中测试连接。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/73738/154743122433629_zh-CN.png)


## 专有网络ECS访问经典网络Redis {#section_obl_1j5_zfb .section}

在该情况下，选择合适的时间将Redis实例切换到专有网络能够让您快速实现互通。相关操作请参见[切换为专有网络](../../../../../cn.zh-CN/用户指南/管理实例/切换为专有网络.md#)。

**说明：** 若ECS与Redis不在同一地域，为了快速使二者连通，可[使用全球多活进行跨地域实例迁移](../../../../../cn.zh-CN/用户指南/迁移数据/云数据库Redis版之间迁移/使用全球多活进行跨地域实例迁移.md#)，将Redis迁移到ECS所在地域。

