# 快速实现不同网络的ECS与Redis实例互访 {#concept_svr_jzt_zfb .concept}

如您的ECS实例在经典网络而 Redis 实例在专有网络（VPC），或 Redis 实例在经典网络而 ECS 实例在专有网络，可根据本文中的办法快速实现互通。

## 背景信息 {#section_i4r_wb5_zfb .section}

阿里云经典网络与专有网络（VPC）为不同的子网，无法直接互通，当环境中 ECS 与 Redis 实例处于不同网络类型中（例如创建实例时选择错误或者业务架构需要调整），并且业务场景需要尽快连通 ECS 和 Redis 时，可考虑切换 Redis 实例的网络类型或者使用 ClassicLink 实现互访。

**说明：** 基于 ClassicLink 互访方案为特殊情况下的临时解决方案，生产环境中为了实现高效缓存，阿里云建议您将 ECS 和 Redis 创建在同一 VPC 网络内。

## 经典网络 ECS 访问专有网络 Redis {#section_vh5_rzt_zfb .section}

您可以通过建立 ClassicLink 连接，使经典网络的ECS实例和专有网络内的 Redis 实例互通。

**前提条件**

-   ECS 与 Redis 实例在同一账号下且在同一地域。
-   专有网络中的网段设置需满足[开启 ClassicLink 的条件](https://help.aliyun.com/document_detail/65412.html)。

**说明：** 若 ECS 与 Redis 不在同一地域，为了快速使二者连通，可[使用全球多活进行跨地域实例迁移](../../../../cn.zh-CN/用户指南/迁移数据/云数据库Redis版之间迁移/使用全球多活进行跨地域实例迁移.md#)，将 Redis 迁移到 ECS 所在地域。

**操作步骤**

1.  登录[云数据库 Redis 版管理控制台](https://kvstore.console.aliyun.com/)。
2.  将 ECS 实例的内网 IP [加入 Redis 实例白名单](../../../../cn.zh-CN/用户指南/管理实例/设置 IP 白名单.md#)。
3.  [建立 ClassicLink 连接](https://help.aliyun.com/document_detail/65413.html)。
4.  在 ECS 中测试连接。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/73738/154391275533629_zh-CN.png)


## 专有网络 ECS 访问经典网络 Redis {#section_obl_1j5_zfb .section}

在该情况下，选择合适的时间将 Redis 实例切换到专有网络能够让您快速实现互通。相关操作请参见[切换为专有网络](../../../../cn.zh-CN/用户指南/管理实例/切换为专有网络.md#)。

**说明：** 若 ECS 与 Redis 不在同一地域，为了快速使二者连通，可[使用全球多活进行跨地域实例迁移](../../../../cn.zh-CN/用户指南/迁移数据/云数据库Redis版之间迁移/使用全球多活进行跨地域实例迁移.md#)，将 Redis 迁移到 ECS 所在地域。

