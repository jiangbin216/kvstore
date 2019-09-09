# Use redis-shake to migrate data from an RDB file {#concept_188715 .concept}

You can use the restore mode of the redis-shake tool to migrate the backup data of an on-premises Redis database to an ApsaraDB for Redis instance, so that you can migrate data from on-premises Redis to the cloud.

## Prerequisites {#section_5yw_woo_qyl .section}

-   An ApsaraDB for Redis instance is created as the destination of data migration.
-   An Elastic Compute Service \(ECS\) instance is created for running the redis-shake tool.
-   The IP address of the ECS instance is added to the whitelist of the destination ApsaraDB for Redis instance.
-   The ECS instance is running the Linux operating system.
-   A backup file is stored in the ECS instance.

## Background {#section_o6o_bml_4mz .section}

The redis-shake tool is an open-source tool developed by Alibaba Cloud. You can use it to parse \(decode mode\), recover \(restore mode\), back up \(dump mode\), and synchronize \(sync/rump mode\) Redis data. In restore mode, the redis-shake tool can use an RDB file to recover or migrate data. This topic describes how to recover data from an RDB file to an ApsaraDB for Redis instance to help you migrate data from on-premises Redis to the cloud.

**Note:** 

-   For more information about the redis-shake tool, see [redis-shake on GitHub](https://github.com/aliyun/redis-shake) or [FAQ](https://github.com/alibaba/RedisShake/wiki/%E7%AC%AC%E4%B8%80%E6%AC%A1%E4%BD%BF%E7%94%A8%EF%BC%8C%E5%A6%82%E4%BD%95%E8%BF%9B%E8%A1%8C%E9%85%8D%E7%BD%AE%EF%BC%9F).

## Procedure {#section_qua_zm1_mx2 .section}

1.  Log on to the ECS instance that can access the destination ApsaraDB for Redis instance.
2.  Download the [redis-shake](https://github.com/alibaba/RedisShake/releases) tool in the ECS instance.

    **Note:** We recommend that you download the latest version.

3.  Run the following command to decompress the downloaded redis-shake.tar.gz package:

    ``` {#codeblock_4gm_ms4_rue}
    # tar -xvf redis-shake.tar.gz
    ```

    **Note:** In the decompressed folder, the redis-shake file is a binary file that can be run in the 64-bit Linux operating system. The redis-shake.conf file is the configuration file of the redis-shake tool. You need to modify this configuration file in the next step.

4.  Modify the redis-shake.conf file. The following table describes the parameters for the restore mode of the redis-shake tool.

    |Parameter|Description|Example|
    |---------|-----------|-------|
    |rdb.input|The path of the RDB file. You can specify either a relative path or an absolute path.|/root/tools/RedisShake/demo.rdb|
    |target.address|The connection address and service port of the destination ApsaraDB for Redis instance.|`r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com:6379`|
    |target.password\_raw|The password of the destination ApsaraDB for Redis instance.|`TargetPass233` **Note:** If you use a database account other than the default database account to connect to the ApsaraDB for Redis instance, set this parameter in the following format: `account:password`.

 |
    |target.db|The database to which the data is recovered in the destination ApsaraDB for Redis instance. Default value: 0. For example, to recover the data of the source on-premises Redis instance to DB10 of the destination ApsaraDB for Redis instance, set this parameter to 10. If you set this parameter to a value less than 0, data is recovered to DB0.|`0`|
    |rewrite|Specifies whether to overwrite the existing keys in the ApsaraDB for Redis instance that are identical to those in the RDB file. Valid values:     -   true
    -   false
 **Note:** Default value: true. We recommend that you back up the valid data of the destination ApsaraDB for Redis instance before migration. If you set this parameter to false and any keys are duplicate in the source and destination databases, an error message is returned.

 |`true`|
    |parallel|The number of concurrent threads used to synchronize the RDB file. More concurrent threads improve synchronization performance. **Note:** 

    -   Minimum value: 1.
    -   Maximum value: depends on the server performance.
    -   Recommended value: 64.
 |64|

    **Note:** You can use the default values for other parameters unless otherwise specified.

5.  Run the following command to recover data:

    ``` {#codeblock_hdd_lmb_jny}
    # ./redis-shake -type=restore -conf=redis-shake.conf
    ```

    **Note:** You must run this command in the same directory as the redis-shake and redis-shake.conf files. Otherwise, you need to specify the correct file path in the command.

    ![](images/45611_en-US.png "Migration example")

    **Note:** When `restore: rdb done` appears in logs, the data is recovered. You can press Ctrl+C to exit the tool.


