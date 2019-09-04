# Step 1: Create an instance {#concept_kqh_vv5_tdb .concept}

This topic describes how to create an ApsaraDB for Redis instance based on your business requirements.

## Procedure {#section_tb5_my5_tdb .section}

1.  Use one of the following methods to open the purchase page:
    -   Open the ApsaraDB for Redis product page and click **Buy Now**.
    -   Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore) and click **Create Instance** in the upper-right corner.
2.  Select a billing method.

    -   **Subscription**: Pay for the service before using. You are charged when you create an instance. This billing method applies to long-term requirements. It is more cost-effective than the Pay-As-You-Go billing method. The longer the duration of the subscription you purchase, the higher the discounts.
    -   **Pay-As-You-Go**: Pay for the service after using. You are charged by hour. This billing method applies to short-term requirements. You can release an instance when it is no longer used to save costs.
    **Note:** You can switch the billing method of an instance from Pay-As-You-Go to subscription. However, you cannot switch the billing method from subscription to Pay-As-You-Go.

3.  Set the following options.

    |Name|Description|
    |----|-----------|
    |Region|Indicates the geo-location where the instance resides. You cannot change the region after you purchase the instance.     -   We recommend that you select a region in close proximity to the geographical location where you reside to garantee the maximum access speed.
    -   Make sure that an ApsaraDB for Redis instance resides in the same region as that of the ECS instance. Otherwise, both instances can only communicate with each other through the Internet rather than the Alibaba Cloud intranet, which may compromise the performance.
 |
    |Zone|Each zone is an independent geographical location that resides in a region. No difference exists between zones.|
    |Network Type|     -   Classic Network: traditional network.
    -   \(Recommended\) VPC: indicates a type of new network provided by Alibaba Cloud. VPC is an abbreviation for Virtual Private Cloud. A VPC provides an isolated network environment with high security and performance over classic networks.
 **Note:** 

    -   Ensure an identical network type for both the ApsaraDB for Redis instance and the ECS instance. Otherwise, the two instances cannot communicate with each other through the Alibaba Cloud intranet.
    -   If you specify VPC as the network type for both the ApsaraDB for Redis instance and the ECS instance, make sure that both instances are in the same VPC. Otherwise, the two instances cannot communicate with each other through the Alibaba Cloud intranet.
    -   You can change the network type of an ApsaraDB for Redis instance from classic network to VPC, see [Set the network type](../../../../reseller.en-US/User Guide/Manage instances/Set the network type.md#). However, you cannot change the network type of ApsaraDB for Redis instance from VPC to classic network.
 |
    |VSwitch|A VSwitch is the basic network module for you to build a VPC. If no VSwitch is available in the VPC, we recommend that you [Create a VSwitch](../../../../reseller.en-US/VPCs and VSwitches/VSwitch management/Create a VSwitch.md#).|
    |Version|Supported versions for an ApsaraDB for Redis instance are listed as follows:     -   2.8
    -   4.0
    -   5.0
 |
    |Node Type|     -   **Dual Copy**: provides a primary-secondary hot standby architecture for persistent data storage.
 |
    |Instance Class|Each class corresponds to a set of configurations, such as the memory size, maximum number of connections, and bandwidth limit. For more information, see [Specifications and performance](../../../../reseller.en-US/Product Introduction/Specifications and performance.md#). **Note:** After you create an instance, a metadatabase is generated and occupies a low amount of storage space.

    -   For a Standard version, the size of the metadatabase is about 32 MB.
    -   For a Cluster version, the size of the metadatabase is calculated as follows: The number of shards included in a cluster × 32 MB.
 |

4.  Enter the **Instance Name** and select the **Quantity**. If you purchase a subscription instance, you need to select the **Duration**.

    **Note:** The connection password can be set after creating the instance, see [Change the password](../../../../reseller.en-US/User Guide/Manage instances/Change the password.md#).

5.  On the right side of the page, click **Buy Now**.
6.  On the Confirm Order page, confirm and select the ApsaraDB for KVStore \(Pay-As-You-Go\) Service Level Agreement \(SLA\).
7.  Click **Activate**.

    **Note:** You will be prompted a message indicating a successful activation after you make the payment. The creation of a new ApsaraDB for Redis instance requires one to five minutes to complete. Then, you can find the new instance in the ApsaraDB for Redis console.


## API operations {#section_e5p_pr4_tgb .section}

|API|Description|
|---|-----------|
|[../../../../dita-oss-bucket/SP\_62/DNREDI1868435/EN-US\_TP\_3181.md\#](../../../../reseller.en-US/API Reference/Lifecycle management/CreateInstance.md#)|Creates an ApsaraDB for Redis instance.|

