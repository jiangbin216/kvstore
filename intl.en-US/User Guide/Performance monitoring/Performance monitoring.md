# Performance monitoring {#concept_zyy_zgv_tdb .concept}

## Background information { .section}

ApsaraDB for Redis provides 10 monitoring groups. You can customize metrics on the ApsaraDB for Redis console based on business requirements, or enable real-time monitoring for ApsaraDB for Redis instances using DMS for Redis.

## Metric descriptions { .section}

|Monitoring group|Data metric|Description|
|----------------|-----------|-----------|
|Basic monitoring group|The basic instance monitoring information|Includes QPS, bandwidth, and memory usage.|
|Keys monitoring group|Monitoring statistics on the use of key value-related commands|Number of times that commands used to delete keys, determine whether a key exists, and perform other such operations are called.|
|String monitoring group|Monitoring statistics on the use of string data-related commands|Number of times that string data commands, such as append and mget, are called.|
|Hashes monitoring group|Monitoring statistics on the use of hash data-related commands|Number of times that hash data commands, such as hget and hdel, are called.|
|Lists monitoring group|Number of times that list data commands, such as blpop and brpop, are called.|Number of times that List data commands, such as blpop and brpop, were called|
|Sets monitoring group|Monitoring statistics on the use of set data-related commands|Number of times that set data commands, such as saadd and scard, are called.|
|Zsets monitoring group|Monitoring statistics on the use of zset data-related commands|Number of times that zset data commands, such as zadd and zcard, are called.|
|HyperLog monitoring group|Monitoring statistics on the use of HyperLogLog data-related commands|Number of times that HyperLogLog data commands, such as pfadd and pfcount, are called.|
|Pub/Sub monitoring group|Monitoring statistics by using commands related to pub/sub functions|Number of times that pub/sub function commands, such as publish and subscribe, are called.|
|Transaction monitoring group|Monitoring statistics on the use of transaction-related commands|Number of times that transaction-related commands, such as watch, multi, and exec, are called.|

## Start real-time monitoring { .section}

1.  Log on to the [Redis console](https://partners-intl.console.aliyun.com/#/kvstore) and locate the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Click **Log on to Database** in the upper right corner.
4.  On the data console logon page, enter the ID and password of the ApsaraDB for Redis instance to go to the homepage of DMS for Redis.
5.  On the Performance Monitoring page, click **Real-time Monitor**.

## Custom metrics { .section}

1.  Log on to the [Redis console](https://partners-intl.console.aliyun.com/#/kvstore) and locate the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Select **Performance Monitoring** in the left-side navigation pane.
4.  Click **Custom Metrics**, select the expected monitoring group, and click **OK**.

## View historical monitoring data { .section}

1.  Log on to the [Redis console](https://partners-intl.console.aliyun.com/#/kvstore) and locate the target instance.
2.  Click the instance ID or **Manage** to go to the **Instance Information** page.
3.  Select **Performance Monitoring** in the left-side navigation pane.
4.  On the Performance Monitoring page, query the historical monitoring data of the instance.

    **Note:** 

    -   You can select a time range to query historical monitoring data.
    -   Cluster instances support viewing of the historical monitoring data of each data node. You can click a data node in **Instance Architecture Diagram** on the Instance Information page or select **Data Node** on the Performance Monitoring page of a cluster instance to query the historical monitoring data of the data node.

