# Through the Internet {#concept_xcl_p2d_5db .concept}

Public endpoints for ApsaraDB for Redis instances are also known as Internet endpoints. You can access an Apsara for Redis instance through the Internet with its public endpoint. However, you may experience high network latency if you use a public endpoint. In production environment, we recommend that you connect to an ApsaraDB for Redis instance through a private endpoint to guarantee high performance of the service.

## Prerequisites {#section_b3b_ih1_mfb .section}

-   The public IP address of an ECS instance or a local host has been added to the whitelist of the ApsaraDB for Redis instance. For more information about how to configure the whitelist, see [Step 2: Set IP whitelists](reseller.en-US/Quick Start/Step 2: Set IP whitelists.md#).
-   For ApsaraDB for Redis 2.8 or 5.0 instances, you cannot apply for public endpoints with the [password-free access](../../../../reseller.en-US/User Guide/Manage instances/Enable password-free access.md#) feature enabled. Please disable password-free access before applying for public endpoints.

    **Note:** For ApsaraDB for Redis 4.0 instances, you can apply for public endpoints after enabling the password-free access feature. At this point, you can access an ApsaraDB for Redis instance from a private endpoint without a password. However, a password is still required to access an ApsaraDB for Redis instance from a public endpoint.


## Scenarios {#section_g59_qpe_v1n .section}

-   **Local access**: You can access an ApsaraDB for Redis instance from a local host.
-   **Cross-account access**: You can access ApsaraDB for Redis instances owned by other Alibaba Cloud accounts from your ECS instance.
-   **Cross-region access**: You can have reciprocal access between an ECS instance and an ApsaraDB for Redis instance. The two instances are owned by the same Alibaba Cloud account, but reside in different regions.
-   **Cross-VPC access**: You can have reciprocal access between an ECS instance and an ApsaraDB for Redis instance. The two instances are owned by the same Alibaba Cloud account and reside in the same region, but in different VPCs.
-   **Cross-network access**: You can have reciprocal access between an ECS instance and an ApsaraDB for Redis instance. The two instances are owned by the same Alibaba Cloud account and reside in the same region but have different network types.

## Pricing {#section_zob_uop_vfl .section}

Public endpoints for ApsaraDB for Redis instances and generated public traffic are free of charge.

## Apply for a public endpoint {#section_hhz_hhj_dhb .section}

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner, on the right side of the Alibaba Cloud trademark, select the region where the target instance resides.
3.  On the Instance List page, click the target instance ID or click **Manage** in the **Actions** column corresponding to the target instance.
4.  On the Instance Information page, click **Apply for External IP Address** in the **Connection Information** area.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/141285/156738906641043_en-US.png)

5.  In the Apply for External IP Address dialog box, enter the endpoint and port number, and click **OK**.
6.  On the Instance Information page, view the **Public Endpoint** in the Connection Information area.

    ![](images/51047_en-US.png "Public endpoints for ApsaraDB for Redis instances")


**Note:** If a public endpoint is no longer used, click **Release Public Endpoint** next to the **Public Endpoint** to release the endpoint.

## Connect to an instance by using a public endpoint {#section_fqq_9my_ssr .section}

You can use DMS, redis-cli, or Redis clients in various languages to connect to the Redis instance. For more information about the connection methods, see the following topics:

-   [Use redis-cli](reseller.en-US/Quick Start/Step 3: Connect to the instance/Use redis-cli.md#)
-   [Use a Redis client](reseller.en-US/Quick Start/Step 3: Connect to the instance/Use a Redis client.md#)

## Resolve connection issues through the public network {#section_y2n_4gp_hb5 .section}

-   Make sure the endpoint you use is the public endpoint rather than the private endpoint. Check[this picture](#fig_riy_05y_hoq) to see where the public endpoint is.
-   You must add the public IP address of a client to the [whitelist of the ApsaraDB for Redis instance](reseller.en-US/Quick Start/Step 2: Set IP whitelists.md#).

