# Switch to VPC {#concept_mtb_nz5_tdb .concept}

## Background {#section_snh_bbg_vdb .section}

ApsaraDB supports two types of networks: classic network and Virtual Private Cloud \(VPC\). The differences between the classic network and VPC are as follows:

-   **Classic network**: Cloud services on a classic network are not isolated. Unauthorized access to a cloud service is blocked only by the security group or whitelist policy of the service.

-   **VPC**: VPC helps you build an isolated network environment in Alibaba Cloud. You can customize the routing table, IP address range, and gateway for a VPC. In addition, you can use a physical connection or Virtual Private Network \(VPN\) to combine your on-premises data center with cloud resources in Alibaba Cloud VPC to build a virtual data center and smoothly migrate your applications to the cloud.


## Precautions {#section_g2p_2bg_vdb .section}

-   You can change the network type from the classic network to VPC, but not vice versa.

-   When changing the network type from the classic network to VPC, you can choose to keep the connection address of the classic network.


## Prerequisites {#section_vnh_bbg_vdb .section}

The network type of an ApsaraDB for Redis instance is the classic network. A VPC and a VSwitch are created in the same region as the ApsaraDB for Redis instance. For more information, see [Create a VPC](../../../../reseller.en-US/VPCs and VSwitches/VPC management/Create a VPC.md#).

**Note:** You must create a VSwitch in the same zone as the target ApsaraDB for Redis instance.

## Procedure {#section_gfs_hbg_vdb .section}

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the top navigation bar, select the region where the target instance is located.
3.  On the Instance List page, click the target instance ID or **Manage** in the **Action** column for the target instance.
4.  On the Instance Information page, click **Switch to VPC Network**.
5.  In the Switch to VPC Network dialog box, select a **VPC** and a **VSwitch**, select an option for **Retain the connection address of the classic network**, select a retention period for **Retention Days**, and then click **OK**.

    **Note:** 

    -   You can click **Refresh** on the **Instance Information** page to view the connection addresses of the classic network and VPC.
    -   If **OK** is dimmed, check whether a **VSwitch** is selected. If no VSwitch is available in the current VPC, you must [Create a VSwitch](../../../../reseller.en-US/VPCs and VSwitches/VSwitch management/Create a VSwitch.md#).

## Related API operations {#section_bx4_1fp_tgb .section}

|API|Description|
|---|-----------|
|[SwitchNetwork](../../../../reseller.en-US/API Reference/Manage instances/SwitchNetwork.md#)|Call this OpenAPI to switch the network type of an ApsaraDB for Redis instance to VPC.|

## Troubleshooting {#section_ynz_jxr_ggb .section}

For more information, see [Troubleshooting for connection issues in ApsaraDB for Redis](../../../../reseller.en-US/FAQs/Troubleshooting for connection issues in ApsaraDB for Redis.md#).

