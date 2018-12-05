# Use AOF to migrate on-premises Redis data to ApsaraDB Redis {#concept_bxn_fbv_vdb .concept}

The redis-cli tool allows you to use AOF to migrate the data of on-premises Redis databases to ApsaraDB Redis.

Redis-cli is the native command line interface of Redis. ApsaraDB Redis allows you to use redis-cli to import data from existing Redis databases to ApsaraDB for Redis for seamless migration. You can also [import data through DTS](intl.en-US/User Guide/Migrate data/Migrate from on-premises Redis to ApsaraDB Redis/Use Data Transmission Service (DTS) to migrate data.md#).

## Notes { .section}

-   Because ApsaraDB Redis supports only access from the Alibaba Cloud intranet, you can perform the following steps only on Alibaba Cloud ECS instances. If your Redis instance is not on an Alibaba Cloud ECS instance, copy the existing AOF to an Alibaba Cloud ECS instance before importing data.

-   Redis-cli is the native command line interface of Redis. If you cannot use redis-cli on your ECS instance, download and install Redis before using redis-cli.


## Procedure { .section}

Perform the following steps if you have created a Redis instance on your Alibaba Cloud ECS instance:

1.  Enable the AOF function on the existing Redis instance \(skip this step if the AOF function has been enabled\).

    ```
    # redis-cli -h old_instance_ip -p old_instance_port config **set** appendonly yes
    ```

2.  Use AOF to import data to an ApsaraDB Redis instance \(assume that the generated AOF is named append.aof\).

    ```
    # redis-cli -h aliyun_redis_instance_ip -p 6379 -a password --pipe < appendonly.aof
    ```

    **Note:** 

    If the AOF function does not need to be enabled for the source Redis instance, you can run the following command to disable the function after data is imported:

    ```
    # redis-cli -h old_instance_ip -p old_instance_port config **set** appendonly no
    ```


