# Upgrade the minor version {#concept_itn_f44_tdb .concept}

Alibaba Cloud has continuously optimized the kernel of ApsaraDB for Redis to fix security vulnerabilities and provide more stable services. You can upgrade the kernel version, which is the minor version, of an ApsaraDB for Redis instance with one click in the console.

## Background { .section}

The method and time required for upgrading the minor version vary with the architecture of an instance:

-   For the cluster edition, read/write splitting edition, or standard disaster recovery edition, the instance is upgraded during cross-server migration. The upgrade duration depends on the data volume. The instance may be disconnected within 30 seconds and become read-only within 60 seconds.
-   For the standard non-disaster recovery edition, the instance is upgraded on the local server. The upgrade takes effect within 5 minutes and has no impact on the ApsaraDB for Redis service. If the resources of the local server are insufficient, cross-server migration is required. The impact is the same as that for the cluster edition.

**Note:** 

-   We recommend that you upgrade the version of an instance during off-peak hours and ensure that your application supports automatic reconnection.
-   The system automatically checks the kernel version of an instance. If the current version is the latest, the **Minor Version Upgrade** button in the upper-right corner of the Basic Information section is dimmed on the Instance Information page of the console for this instance.

## Procedure { .section}

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the top navigation bar, select the region where the target instance is located.
3.  On the Instance List page, click the target instance ID or **Manage** in the **Action** column for the target instance.
4.  On the Instance Information page, click **Minor Version Upgrade**.

     

5.  In the Minor Version Upgrade dialog box, click **Upgrade Now**.

     

    In the Basic Information section, the instance status is **Upgrading a minor version**. When the instance status changes to **Available**, the upgrade is completed.

     

     


