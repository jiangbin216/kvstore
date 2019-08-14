# Step 2: Set IP whitelists {#concept_lmv_qhf_vdb .concept}

To ensure database security and stability, before using an ApsaraDB for Redis instance, you must add one or more IP addresses or CIDR blocks that you use to connect to databases to a whitelist group of the instance. We recommend that you periodically check and adjust your whitelists to improve the access security protection and secure data in ApsaraDB for Redis.

## Prerequisites {#section_snn_3jf_vdb .section}

The whitelist feature is applicable to certain kernel versions. If the kernel version of the instance does not support the whitelist feature, the system displays a prompt when you set a whitelist. In this case, you need to upgrade the minor version to the latest version. For more information, see [Upgrade a minor version](../reseller.en-US/User Guide/Manage instances/Upgrade a minor version.md#).

## Procedure {#section_op5_3jf_vdb .section}

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  On the menu bar, select the region where the target instance is located.
3.  On the Instance List page, click the target instance ID, or click **Manage** in the **Action** column next to the target instance.
4.  The Instance Information page is displayed by default. In the left-side navigation pane, click **Whitelist Settings**.
5.  On the Whitelist Settings page, continue with one of these methods:
    -   To customize the whitelist group name, create a new whitelist group:
        1.  Click **Add a Whitelist Group** in the upper-right corner.
        2.  In the Add a Whitelist Group dialog box that appears, set **Group Name**.

            **Note:** A group name must be 2 to 32 characters in length and contain lowercase letters, digits, or underscores \(\_\). The group name must start with a lowercase letter and end with a letter or digit. You cannot change this name after you create the whitelist group.

    -   If you do not require a custom whitelist group, click **Modify** next to the target whitelist group.
6.  In the Add a Whitelist Group or Modify Whitelist of Group dialog box that appears, continue with one of these methods:
    -   Manually modify the **Whitelist of Group** field:
        1.  In the **Whitelist of Group** field, enter the IP addresses or CIDR blocks that you can use to connect to the ApsaraDB for Redis instance.

            ![](../DNREDI1849435/images/46644_en-US.png "Manually modify the whitelist group")

            **Note:** 

            -   Set the whitelist to `0.0.0.0/0` to allow connections from all IP addresses.
            -   Set the whitelist to `127.0.0.1` to block connections from all IP addresses.
            -   Set the whitelist to a CIDR block to allow connections from the IP addresses within the CIDR block, such as `10.10.10.0/24`.
            -   When you enter multiple IP addresses or CIDR blocks, separate them with commas \(,\) and leave no space before or after each comma.
            -   You can add 1,000 or fewer IP addresses or CIDR blocks to each whitelist group.
        2.  Click **OK**.
    -   Load internal IP addresses of target ECS instances under the current Alibaba Cloud account:
        1.  Click **Load ECS Internal IP Addresses**.

            ![](../DNREDI1849435/images/46645_en-US.png "Load internal IP addresses of target ECS instances")

        2.  Select internal IP addresses of target ECS instances.

            ![](../DNREDI1849435/images/46642_en-US.png "Select internal IP addresses of target ECS instances")

            **Note:** You can perform a fuzzy search by ECS instance name, ID, or IP address on the search bar above the list of ECS internal IP addresses.

        3.  Click **OK**.

## API operations {#section_mgb_vw4_tgb .section}

|Operation|Description|
|---------|-----------|
|[../DNREDI1868435/EN-US\_TP\_3192.md\#](../reseller.en-US//DescribeSecurityIps.md#)|Call this OpenAPI to query IP addresses or CIDR blocks that you can use to connect to a specified ApsaraDB for Redis instance.|
|[../DNREDI1868435/EN-US\_TP\_3197.md\#](../reseller.en-US//ModifySecurityIps.md#)|Call this OpenAPI to set IP whitelists of a specified ApsaraDB for Redis instance.|

