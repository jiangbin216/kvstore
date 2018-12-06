# Migrate data from an on-premises Redis cluster to an ApsaraDB Redis cluster {#concept_tf4_bbv_vdb .concept}

You can use redis-sync-manager to migrate data from an on-premises Redis cluster to an ApsaraDB Redis cluster.

## Prerequisites {#section_q3l_2xh_wfb .section}

-   You have specified redis-port in the $PATH environment variable, because redis-sync-manager depends on [redis-port](intl.en-US/User Guide/Migrate data/Migrate from on-premises Redis to ApsaraDB Redis/暂时只有中文.md#) for the migration.
-   You must be aware of the possible memory usage requirements for source and target basic data, and the current concurrency.
-   Make sure that no slots in the source cluster are in an intermediate migration state.

## Migration tools { .section}

-   Redis-port: is used to synchronize data from a single Redis process to the target ApsaraDB for Redis cluster.
-   Redis-sync-manager: serves as a supplement to redis-port \(redis-port is encapsulated in redis-sync-manager\) and is used to synchronize data from the source Redis cluster to the target ApsaraDB for Redis cluster.

## Download the tool { .section}

[Redis-sync-manager](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/94155/cn_zh/1542707688880/redis-sync-manager)

## Instructions { .section}

Run the following command to migrate data from a user-created Redis cluster to an ApsaraDB for Redis cluster:

```
./redis-sync-manager --from=src_host:src_port --target=dst_host:dst_port [--password=src_password]  [--auth=dst_password] [--filterkey="str1|str2|str3"] [--targetdb=DB] [--rewrite] [--bigkeysize=SIZE] [--logfile=REDISPORT.LOG] [--httpport=HTTPPORT] [--sync-parallel=INT] [--sync-role="master|slave"]
```

**Migration mechanism of redis-sync-manager**

Redis-sync-manager interacts with `src_host:src_port` to obtain information about the cluster topology through the `cluster nodes` command first. Then, a `IP:PORT` list of the shards to be synchronized is returned based on the `--sync-role` parameter setting. Finally, redis-sync-manager calls redis-port to synchronize data. \(The concurrency of full data synchronization depends on the `--sync-parallel` parameter setting, and incremental data of each shard in the source cluster is synchronized to the corresponding shard in the target cluster.\) The following table describes the related parameters.

|Parameter|Description|
|---------|-----------|
|src\_host|The domain name or IP address of the user-created Redis database. Set this parameter to the IP address of a process in the user-created Redis cluster.|
|src\_port|The port of the user-created Redis database. Set this parameter to the port that corresponds to the IP address specified for src\_host.|
|src\_password|The password of the user-created Redis database.|
|dst\_host|The domain name of the ApsaraDB for Redis database.|
|dst\_port|The port of the ApsaraDB for Redis database.|
|dst\_password|The password of the ApsaraDB for Redis database.|
|str1|str2|str3|Filters keys with str1, str2, or str3.|
|DB|The database to be synchronized to ApsaraDB for Redis.|
|rewrite|Overwrites a key that has already been written.|
|bigkeysize=SIZE|Indicates that when the written value is greater than SIZE, the big key write mode is used.|
|--logfile=REDISPORT.LOG|The name of a log file, for example, edis-sync-manager.log. During migration, different log files are generated for the migrated shards, and the serial number of the shard that is being migrated is automatically added to the name of its corresponding log file. Default value: `logs/redis-sync-manager.log`.|
|--sync-parallel=INT|Indicates whether concurrency is supported for data synchronization and displays the possible memory usage. Default value: `1`.|
|--sync-role="master|slave"|Indicates the synchronization order of primary or secondary database of the source cluster. Default value: `master`.|

## Migration example {#ul_lfs_1y4_k2b .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15449/15440671566883_en-US.png)

The callouts in the picture are described as follows.

1.  The synchronized information and synchronization status of each shard are displayed.
2.  An `IP:PORT` is selected for each shard based on the `--sync-role` parameter setting, and the IP:PORTs are printed out one by one.
3.  The synchronization status of each shard is printed to the log file.

