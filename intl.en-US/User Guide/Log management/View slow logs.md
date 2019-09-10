# View slow logs {#concept_nw5_xmv_rfb .concept}

In the ApsaraDB for Redis console, you can view slow logs in a specified period to find clues to resolve performance issues and optimize requests.

## Background {#section_jfk_4qv_rfb .section}

ApsaraDB for Redis uses slow logs to record requests that are run for a long time. If a command is run for a longer time than the threshold specified by the slowlog-log-slower-than parameter \(in microseconds\), the command is recorded in a slow log. In ApsaraDB for Redis, the default value of the slowlog-log-slower-than parameter is 10,000 μs, that is, 10 ms.

The slowlog-max-len parameter specifies the maximum number of slow logs stored by an ApsaraDB for Redis instance. By default, an ApsaraDB for Redis instance stores 128 slow logs.

**Note:** For more information about how to set this parameter, see [Parameter settings ](reseller.en-US/User Guide/System Parameters/Parameter settings .md#). We do not recommend that you modify the default value of the slowlog-log-slower-than parameter unless necessary.

To view slow logs of an instance, you can log on to the ApsaraDB for Redis console and choose Logs \> Slow Logs from the left-side navigation pane.

## View slow logs on the console {#section_yjt_bsv_rfb .section}

**Limits**

-   The engine version of the ApsaraDB for Redis instance is Redis 4.0 or later.
-   The minor version of the ApsaraDB for Redis instance is the latest.
-   **Note:** If your instance version does not meet the conditions for querying slow logs and you need to upgrade the version to use the slow log feature, upgrade the major or minor version as needed. For more information, see [Upgrade the minor version](reseller.en-US/User Guide/Manage instances/Upgrade the minor version.md#) and [Upgrade the major version](reseller.en-US/.md#).


**Procedure**

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the top navigation bar, select the region where the target instance is located.
3.  On the Instance List page, click the target instance ID or **Manage** in the **Action** column for the target instance.
4.  On the Instance Information page, choose **Logs** \> **Slow Logs** from the left-side navigation pane.
5.  On the Slow Logs page, click the calendar icon next to **Query Time**, select a time option or set **Start Time** and **End Time**, and then click **OK**.

    ![View slow logs in Logs of the console](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/41691/156808454936254_en-US.png)

    **Note:** If you use an ApsaraDB for Redis instance of the cluster edition, you can click **Data nodes** next to **Query Time** and select the target node.


