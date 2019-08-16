# Enable password-free access {#concept_ttq_dst_j2b .concept}

ApsaraDB for Redis supports password-free access in VPCs to achieve more convenient database connections while ensuring security. To enable password-free access, ensure that ECS instances and ApsaraDB for Redis instances are in the same VPC. This way, the ECS instances can access ApsaraDB for Redis instances without the need to use a password. At the same time, the username and password can also be used to connect to the ApsaraDB for Redis instances.

## Prerequisites {#section_2gi_7c8_rol .section}

-   The network type of the instance is VPC.
-   The client and instance are in the same VPC.
-   The whitelist has been set for the instance. To secure access, you cannot add 0.0.0.0/0 to the whitelist to allow any access.

## Limits {#section_br8_hg0_6f2 .section}

-   Public endpoints can be used to access ApsaraDB for Redis 4.0 instances while VPC password-free access is enabled. In this case, you do not need to use a password to access ApsaraDB for Redis instances if an internal endpoint is used. However, you still need a password if a public endpoint is used.

    **Note:** If a public endpoint fails to access ApsaraDB for Redis 4.0 instances while VPC password-free access is enabled, upgrade the kernel version, see [Upgrade the minor version](reseller.en-US/User Guide/Manage instances/Upgrade the minor version.md#).

-   Public endpoints are unavailable for instances of ApsaraDB for Redis 2.8 and ApsaraDB for Redis 5.0 while VPC password-free access in enabled.

## Procedure {#section_ugs_sio_csy .section}

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the homepage, select the region where the instance is located.
3.  On the Instance Information page, click the instance ID, or click **Manage** in the **Actions** column corresponding to the instance.
4.  On the Instance Information page, find the Connection Information section and click **Enable Password-free Access**.
5.  In the message that appears, click **OK**.

Refresh the Instance Information page. **Disable Password-free Access** is displayed. You can click **Disable Password-free Access** if password-free access is not necessary. However, applications that use the password-free access function cannot connect to databases if this function is disabled. Exercise caution when you disable this function.

**Note:** If your application is already connected to the instance before password-free access is enabled, restart the application and reconnect to the ApsaraDB for Redis instance for this function to take effect.

## Related operations {#section_lh5_zmp_tgb .section}

|Operation|Description|
|---------|-----------|
|[ModifyInstanceVpcAuthMode](../../../../reseller.en-US/API Reference/Network security/ModifyInstanceVpcAuthMode.md#)|Enable or disable password-free access.|

