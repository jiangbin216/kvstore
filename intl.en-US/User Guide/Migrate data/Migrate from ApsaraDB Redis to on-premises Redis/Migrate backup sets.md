# Migrate backup sets {#concept_np4_myf_vdb .concept}

You can use the redis-port tool to migrate ApsaraDB for Redis backup sets to an on-premises Redis database.

## Downloading backup set data from the ApsaraDB Redis console { .section}

1.  Log on to the [ApsaraDB Redis console](https://kvstore.console.aliyun.com/) and locate the target instance on the **Instance List** page.
2.  Click the instance ID, or click the vertical dots in the Action column and choose **Manage** from the shortcut menu, to go to the Instance Information page.
3.  View the number of DB nodes in Architecture Diagram.
4.  On the Backup and Recovery page, download backup set data based on the number of DB nodes.

## Download redis-port { .section}

[Redis-port address](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/66008/cn_zh/1526545851725/redis-port)

## Example { .section}

```
./redis-port  restore  --input=x/dump.rdb  --target=dst\_host:dst\_port   --auth=dst\_password  [--filterkey="str1|str2|str3"] [--targetdb=DB] [--rewrite] [--bigkeysize=SIZE] [--logfile=REDISPORT.LOG]
```

**Note:** 

You need to perform the recovery procedure once for the backup set of each database.

**Parameter description**

-   x/dump.rdb: indicates the dump file path of an ApsaraDB for Redis backup set.
-   dst\_host: indicates the domain name or IP address of the user-created Redis database.
-   dst\_port: indicates the port of the user-created Redis database.
-   dst\_password: indicates the password of the user-created Redis database.
-   str1|str2|str3: filters keys with str1, str2, or str3.
-   DB: indicates the database to be synchronized to the user-created Redis database.
-   rewrite: overwrites a key that has already been written.
-   bigkeysize=SIZE: indicates that when the written value is greater than SIZE, the big key write mode is used.

## Check the data recovery status based on the redis-port log { .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3153/15439937272663_en-US.png)

When `restore: rdb done` appears, data recovery is completed.

