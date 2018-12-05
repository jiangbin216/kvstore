# Use RDB files to migrate from on-premises Redis to ApsaraDB Redis {#concept_xnh_dk1_wdb .concept}

The redis-port tool allows you to use RDB files to synchronize the data of an on-premises Redis database to ApsaraDB Redis.

## Download redis-port { .section}

[Redis-port address](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/85829/cn_zh/1533199526614/redis-port%282%29)

## Example { .section}

```
./redis-port  restore  --input=x/dump.rdb  --target=dst_host:dst_port   --auth=dst_password  [--filterkey="str1|str2|str3"] [--targetdb=DB] [--rewrite] [--bigkeysize=SIZE] [--logfile=REDISPORT.LOG]
```

**Parameter description**

-   x/dump.rdb: indicates the dump file path of the user-created Redis database.
-   dst\_host: indicates the domain name of the ApsaraDB for Redis database.
-   dst\_port: indicates the port of the ApsaraDB for Redis database.
-   dst\_password: indicates the password of the ApsaraDB for Redis database.
-   str1|str2|str3: filters keys with str1, str2, or str3.
-   DB: indicates the database to be synchronized to ApsaraDB for Redis.
-   rewrite: overwrites a key that has already been written.
-   bigkeysize=SIZE: indicates that when the written value is greater than SIZE, the big key write mode is used.

## Check the data synchronization status based on the redis-port log { .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3158/15439933662802_en-US.png)

When `restore: rdb done` appears, data synchronization is completed.

