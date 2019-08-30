# Use redis-cli {#concept_tzm_xdd_5db .concept}

You can use the Redis command-line interface \(redis-cli\) to connect to ApsaraDB for Redis.

## Introduction to redis-cli {#section_qf7_03r_ej7 .section}

Redis-cli is a command-line tool included in the Redis software distribution. You can use redis-cli to connect to an ApsaraDB for Redis instance and send commands to the instance to manage data.

With redis-cli, you can connect to an ApsaraDB for Redis instance from an ECS instance running Linux through the Alibaba Cloud intranet, or from a local host through the Internet. Accessing ApsaraDB for Redis through the Alibaba Cloud intranet provides higher security and performance.

To access an ApsaraDB for Redis instance from a local host through the public network, you must follow the instructions in [Connect to an ApsaraDB for Redis instance over the public network](reseller.en-US/Quick Start/Step 3: Connect to the instance/Through the Internet.md#) to apply for a public endpoint. Then, you can follow the instructions in the [How to connect](#section_6lt_lnn_hoc) section of this topic to connect to the instance.

## Install redis-cli {#section_031_oyo_yas .section}

Install the Redis software distribution that includes redis-cli in Linux. For more information, see [Redis community](https://redis.io/download).

## Prerequisites {#section_77f_hlc_he4 .section}

Connect through the Alibaba Cloud intranet

-   If the network type for both the ECS instance and the ApsaraDB for Redis instance is VPC, the two instances must reside in the same VPC of a region.
-   If the network type for both the ECS instance and the ApsaraDB for Redis instance is classic network, the two instances must reside in the same region.
-   You have added the private IP address of an ECS instance to the whitelist of an ApsaraDB for Redis instance.
-   You have installed the Redis software distribution on the ECS instance.

Connect through the Internet

-   The ApsaraDB for Redis instance has a public endpoint. For more information, see [Connect to an ApsaraDB for Redis instance over the public network](reseller.en-US/Quick Start/Step 3: Connect to the instance/Through the Internet.md#).
-   You have added the public IP address of the local host to a [whitelist](reseller.en-US/Quick Start/Step 2: Set IP whitelists.md#) of the ApsaraDB for Redis instance.
-   The operating system of the local host must be Linux.
-   You have installed the Redis software distribution on the local host.

## Precautions {#section_mcy_165_vfk .section}

-   If you access an ApsaraDB for Redis instance from its private endpoint with the [VPC password-free access](../../../../reseller.en-US/User Guide/Manage instances/Enable password-free access.md#) feature enabled, you can access the instance without a password.
-   If you access an ApsaraDB for Redis instance from its public endpoint with the [VPC password-free access](../../../../reseller.en-US/User Guide/Manage instances/Enable password-free access.md#) feature enabled, a password is still required for accessing the instance.

## How to connect {#section_6lt_lnn_hoc .section}

You can use the following command to connect to an ApsaraDB for Redis instance.

``` {#codeblock_1li_ojv_huq}
redis-cli -h <host> -p <port> -a <password>
```

|Name|Description|
|----|-----------|
|-h| Specifies the endpoint of the ApsaraDB for Redis instance.

 -   Access an ApsaraDB for Redis instance through the Alibaba Cloud intranet, use an [private endpoint](../../../../reseller.en-US/User Guide/Connection management/View the connection address of an ApsaraDB for Redis instance.md#).
-   Access an ApsaraDB for Redis instance through the Internet, use a [public endpoint](reseller.en-US/Quick Start/Step 3: Connect to the instance/Through the Internet.md#).

 |
|-p| Specifies the service port of the ApsaraDB for Redis instance.

 -   The default port number is 6379. You cannot change the port number.

 |
|-a|Set the password for the ApsaraDB for Redis instance. You can skip this parameter to avoid displaying a password in plain text to enhance security. After running the preceding command, you can enter `auth <password>` to complete the authentication. The following figure shows an example.|

![](images/51171_en-US.png "Command example")

