# Use redis-shake to migrate data under the same account {#concept_226440 .concept}

You can use the rump mode of the redis-shake tool to migrate data from an ApsaraDB for Redis instance to another ApsaraDB for Redis instance under the same Alibaba Cloud account.

## Prerequisites {#section_pi3_gr7_2eg .section}

-   An ApsaraDB for Redis instance is created as the destination of data migration.
-   An Elastic Compute Service \(ECS\) instance is created for running the redis-shake tool.
-   The IP address of the ECS instance is added to the whitelists of both the source and destination ApsaraDB for Redis instances.
-   The ECS instance is running the Linux operating system.

## Background {#section_uv4_c4p_8xh .section}

The redis-shake tool is an open-source tool developed by Alibaba Cloud. You can use it to parse \(decode mode\), recover \(restore mode\), back up \(dump mode\), and synchronize \(sync/rump mode\) Redis data. In rump mode, the redis-shake tool can scan the source Redis to obtain full data and write the data to the destination Redis to migrate data. This migration solution does not use the SYNC or PSYNC command, and therefore has little impact on the service performance of Redis. It applies to Redis clusters and can be widely used to migrate data between on-premises Redis and ApsaraDB for Redis. This topic describes how to migrate data from an ApsaraDB for Redis instance to another ApsaraDB for Redis instance under the same Alibaba Cloud account.

**Note:** 

-   The rump mode does not support incremental migration. We recommend that you stop writing data to the source Redis before migration to prevent data inconsistency.
-   The rump mode supports data migration between different Redis versions, such as from Redis 2.8 to Redis 4.0.
-   The rump mode supports data migration between different cloud products. In this case, either the source or destination must support Internet access.
-   For more information about the redis-shake tool, see [redis-shake on GitHub](https://github.com/aliyun/redis-shake) or [FAQ](https://github.com/alibaba/RedisShake/wiki/%E7%AC%AC%E4%B8%80%E6%AC%A1%E4%BD%BF%E7%94%A8%EF%BC%8C%E5%A6%82%E4%BD%95%E8%BF%9B%E8%A1%8C%E9%85%8D%E7%BD%AE%EF%BC%9F).

## Procedure {#section_0ne_wlk_e5d .section}

1.  Log on to the ECS instance that can access both the source and destination ApsaraDB for Redis instances.
2.  Download the [redis-shake](https://github.com/alibaba/RedisShake/releases) tool in the ECS instance.

    **Note:** We recommend that you download the latest version.

3.  Run the following command to decompress the downloaded redis-shake.tar.gz package:

    ``` {#codeblock_os5_5t1_5yd}
    # tar -xvf redis-shake.tar.gz
    ```

    **Note:** In the decompressed folder, the redis-shake file is a binary file that can be run in the 64-bit Linux operating system. The redis-shake.conf file is the configuration file of the redis-shake tool. You need to modify this configuration file in the next step.

4.  Modify the redis-shake.conf file. The following table describes the parameters for the rump mode of the redis-shake tool.

    |Parameter|Description|Example|
    |---------|-----------|-------|
    |source.address|The connection address and service port of the source ApsaraDB for Redis instance.|`r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com`|
    |source.password\_raw|The password of the source ApsaraDB for Redis instance.|`SourcePass233` **Note:** If you use a database account other than the default database account to connect to the ApsaraDB for Redis instance, set this parameter in the following format: `account:password`.

 |
    |target.address|The connection address and service port of the destination ApsaraDB for Redis instance.|`r-j6cxxxxxxxxxxxxx.redis.rds.aliyuncs.com`|
    |target.password\_raw|The password of the destination ApsaraDB for Redis instance.|`TargetPass233`|
    |rewrite|Specifies whether to overwrite the existing keys in the ApsaraDB for Redis instance that are identical to those in the RDB file. Valid values:     -   true
    -   false
 **Note:** Default value: true. We recommend that you back up the valid data of the destination ApsaraDB for Redis instance before migration. If you set this parameter to false and any keys are duplicate in the source and destination databases, an error message is returned.

 |`true`|
    |scan.key\_number|The number of keys that the redis-shake tool obtains each time it scans the source ApsaraDB for Redis instance. If you do not set this parameter, the default value 100 is used.|`100`|
    |scan.special\_cloud|The cloud of the source Redis instance.|`aliyun_cluster` **Note:** The example indicates that the data is migrated from the source ApsaraDB for Redis instance of the cluster edition.

 |

5.  Run the following command to migrate data:

    ``` {#codeblock_5iu_0n5_d0a}
    # ./redis-shake -type=rump -conf=redis-shake.conf
    ```

    **Note:** You must run this command in the same directory as the redis-shake and redis-shake.conf files. Otherwise, you need to specify the correct file path in the command.

    ![Use redis-shake to migrate data under the same account](images/46084_en-US.png "Migration example")

    **Note:** When the message framed in red in the preceding figure appears, the data is migrated. After migration is completed, you can use the redis-full-check tool to check whether the data is consistent between the source and destination databases. For more information, see [Verify migrated data](reseller.en-US/User Guide/Migrate data/Verify migrated data.md#).


