# Modify the port for the public endpoint {#concept_1062613 .concept}

You can customize a port that ranges from 1024 to 65535 for the public endpoint of an ApsaraDB for Redis instance.

**Note:** You cannot modify ports for internal endpoints.

## Prerequisites {#section_xoy_ri4_ltk .section}

-   The ApsarDB for Redis instance is running.
-   The public endpoint of the ApsaraDB for Redis instance is available. If the public endpoint is not available, click [Apply](../../../../reseller.en-US/Quick Start/Step 3: Connect to the instance/Through the Internet.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/855971/156758844251176_en-US.png)

-   The [Whitelist](../../../../reseller.en-US/Quick Start/Step 2: Set IP whitelists.md#) of the ApsaraDB for Redis instance includes IP addresses other than 127.0.0.1. After the whitelist is modified, the Instance Information page displays **Modify Public Endpoint**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/855971/156758844251177_en-US.png)


## Procedure {#section_ofg_zf7_kk5 .section}

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the homepage, select the region where the instance is located.
3.  On the Instance Information page, click the instance ID, or click **Manage** in the **Action** column corresponding to the instance.
4.  In the **Connection Information** section, click **Modify Public Endpoint**.
5.  In the Modify Public Endpoint dialog box that appears, set **Connection Type** to **Public Endpoint**. Set **Port**. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/855971/156758844251059_en-US.png)


## Impacts of the modification {#section_g6e_u61_kwx .section}

After the port is modified, you need to use the new port when you access the ApsaraDB for Redis instance through the Internet. Ensure that the setting for the application is modified accordingly.

