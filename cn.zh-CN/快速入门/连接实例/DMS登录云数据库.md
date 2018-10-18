# DMS登录云数据库 {#concept_jvw_c24_tdb .concept}

数据管理DMS（Data Management）是一款访问管理云端数据的Web服务，支持Redis、 MySQL、SQL Server、PostgreSQL和 MongoDB 等数据源。DMS提供了数据管理、对象管理、数据流转和实例管理四部分功能。

您可以通过以下两种方式使用DMS登录数据库。

## 从Redis管理控制台登录 {#section_am5_r11_kfb .section}

**操作步骤**

1.  登录[Redis管理控制台](https://kvstore.console.aliyun.com/)。
2.  在实例列表中，单击目标实例右侧操作栏的**管理**，或者单击**实例ID**。
3.  在实例信息页，单击右上方的**登录数据库**。

    **说明：** 

    -   通过该方式打开DMS，系统会自动填写登录页面中的数据库连接地址，您只要输入密码即可。
    -   如果实例开启了[免密访问](../../../../cn.zh-CN/用户指南/管理实例/开启免密访问.md#)功能，则在同一VPC内无需提供密码信息即可连接数据库。

## 从DMS管理控制台登录 {#section_hfv_w11_kfb .section}

**操作步骤**

1.  登录 [DMS管理控制台](https://dms-rds.aliyun.com)。
2.  输入要登录的数据库连接地址和密码，单击**登录**，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3127/15398507211079_zh-CN.png)

    **说明：** 

    -   连接信息可以在[Redis管理控制台](https://kvstore.console.aliyun.com/) 的实例信息页获取。
    -   经典网络及VPC网络的实例都支持DMS。使用DMS登录VPC网络中的实例时，系统需要申请一条特殊通道，所以该类实例在第一次登录时，会有短暂的等待时间。

更多的DMS相关信息请参见[DMS官方文档](https://help.aliyun.com/product/26590.html)。

