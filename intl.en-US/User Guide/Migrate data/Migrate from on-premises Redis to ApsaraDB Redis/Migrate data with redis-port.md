# Migrate data with redis-port {#concept_u3d_fj1_wdb .concept}

You can use redis-port to migrate data from a self-managed Redis database to an ApsaraDB for Redis instance.

## Prerequisites {#section_vcm_32p_1gb .section}

-   You have created a Linux-based Elastic Compute Service \(ECS\) instance in the VPC where the target ApsaraDB for Redis instance resides.
-   You have downloaded [redis-port](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/85829/cn_zh/1533199526614/redis-port%282%29?spm=a2c4g.11186623.2.10.1b5447ceE6Wtwt) tool in the ECS instance mentioned above.
-   You have run `chmod u+x redis-port` to change redis-port into an executable file.

## Procedure { .section}

1.  Log in to the Linux system built in your ECS instance.
2.  In the directory where redis-port resides, run below code to start the migration.

    ```language-bourne
    ./redis-port sync --from=src_host:src_port --Password=src_password --target=dst_host:dst_port --auth=dst_password [--filterkey="str1|str2|str3"] [--targetdb=dB] [--rewrite] [--bigkeysize=size] [--logfile=redisport.log]
    ```

    |Argument|Description|
    |--------|-----------|
    |src\_host|Domain name \(or IP\) of the self-managed Redis database.|
    |src\_port|Port of the self-managed Redis database.|
    |src\_password|Password of the self-managed Redis database.|
    |dst\_host|Domain name of the ApsaraDB for Redis instance.|
    |dst\_port|Port of the ApsaraDB for Redis instance.|
    |dst\_password|Password of the ApsaraDB for Redis instance.|
    |str1|str2|str3|Filter keys with str1, str2, or str3.|
    |DB|Index of the self-managed Redis DB to be migrated.|
    |rewrite|Overwrite identical keys that already exist in the ApsaraDB for Redis instance.|
    |bigkeysize=SIZE|While writing keys larger than the value of SIZE, enable big-key writing.|
    |logfile|Specify a file to save the logs.|

3.  Monitor the logs to make sure the migration procedure runs as expected.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3157/15441533652803_en-US.png)


