# Upgrade the major version {#task_ast_xh3_3gb .task}

You can upgrade the engine version, which is the major version, of an ApsaraDB for Redis instance with one click in the console. For example, you can upgrade the major version from Redis 2.8 to Redis 4.0.

The engine version of an instance is not the latest.

ApsaraDB for Redis provides some features only for specific engine versions. If the engine version of your instance is too earlier, you can follow the procedure in this topic to upgrade the version.

The method and time required for upgrading the major version vary with the architecture of an instance:

-   For the cluster edition, read/write splitting edition, or standard disaster recovery edition, the instance is upgraded during cross-server migration. The upgrade duration depends on the data volume. The instance may be disconnected within 30 seconds and become read-only within 60 seconds.
-   For the standard non-disaster recovery edition, the instance is upgraded on the local server. The upgrade takes effect within 5 minutes and has no impact on the ApsaraDB for Redis service. If the resources of the local server are insufficient, cross-server migration is required. The impact is the same as that for the cluster edition.

**Note:** We recommend that you upgrade the version of an instance during off-peak hours and ensure that your application supports automatic reconnection.

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the top navigation bar, select the region where the target instance is located.
3.  On the Instance List page, click the target instance ID or **Manage** in the **Action** column for the target instance.
4.  On the Instance Information page, click **Major Update** in the upper-right corner of the Basic Information section. 

    ![Upgrade the major version of an instance](images/35955_en-US.png "Upgrade the major version")

5.  In the Major Update dialog box, select the target version. 
6.  Select **Update Now** or **Update During Maintenance** as required, and then click **OK**. 

    **Note:** We recommend that you set the [maintenance window](reseller.en-US/User Guide/Manage instances/Set a maintenance window.md#) to a period during off-peak hours and select **Update During Maintenance** to minimize the impact on normal business during the upgrade.

    **Related API operations**

    [ModifyInstanceMajorVersion](../../../../reseller.en-US/API Reference/Manage instances/ModifyInstanceMajorVersion.md#)


