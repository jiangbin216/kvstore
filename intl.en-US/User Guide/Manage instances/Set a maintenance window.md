# Set a maintenance window {#concept_sjv_kpl_vdb .concept}

## Background {#section_mxr_3ql_vdb .section}

To ensure the stability of ApsaraDB for Redis instances on the Alibaba Cloud platform, the backend system maintains instances and servers occasionally.

Before the maintenance, ApsaraDB for Redis sends short message service \(SMS\) messages and emails to contacts configured under your Alibaba Cloud account.

To guarantee the stability of the maintenance process, instances enter the **Maintaining Instance** status before the preset maintenance window on the day of maintenance. When an instance is in this status, data in the database can still be accessed. However, change operations such as configuration change are temporarily unavailable for this instance in the console, whereas query operations such as performance monitoring are still available.

**Note:** 

During the preset maintenance window, instances may be disconnected in the process of maintenance. We recommend that you set the maintenance window to a period during off-peak hours.

## Procedure { .section}

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the top navigation bar, select the region where the target instance is located.
3.  On the Instance List page, click the target instance ID or **Manage** in the **Action** column for the target instance.
4.  On the Instance Information page, click **Settings** to the right of the **Maintenance Window** field in the Basic Information section.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3144/15680865792169_en-US.png)

5.  Select a period and click **Save**.

    **Note:** 

    The time is UTC+8.


## Related API operations {#section_hvq_ncp_tgb .section}

[../../../../dita-oss-bucket/SP\_62/DNREDI1868435/EN-US\_TP\_3195.md\#](../../../../reseller.en-US/API Reference/Manage instances/ModifyInstanceMaintainTime.md#)

