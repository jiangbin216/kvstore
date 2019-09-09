# Verify migrated data {#concept_221787 .concept}

After Redis data is migrated, you can check whether the data is consistent between the source and destination Redis instances.

## Prerequisites {#section_5yw_woo_qyl .section}

-   Redis data is migrated.
-   An Elastic Compute Service \(ECS\) instance is created to run the redis-full-check tool.
-   The IP address of the ECS instance is added to the whitelists of both the source and destination Redis instances.
-   The ECS instance is running the Linux operating system.
-   Git and Golang are installed in the ECS instance.

## Background {#section_vvi_yl8_qlf .section}

If an exception occurs during Redis data migration, the data is inconsistent between the source and destination Redis instances. You can use the redis-full-check tool to locate abnormal data, which provides a reliable basis for data alignment.

The redis-full-check tool is a Redis data verification tool developed by Alibaba Cloud. It can extract data from the source and destination instances, compare them for multiple times, and then record the comparison results in a SQLite3 database. This tool can be used to verify full data.

**Note:** For more information about the redis-full-check tool, see [redis-full-check on GitHub](https://github.com/alibaba/RedisFullCheck).

## Procedure {#section_lbp_vn1_cdn .section}

1.  Log on to the ECS instance that can access the destination Redis instance.
2.  Clone the redis-full-check tool to the ECS instance.

    ``` {#codeblock_wca_cgc_wnx}
    # git clone https://github.com/alibaba/RedisFullCheck.git
    ```

3.  Go to the RedisFullCheck directory and set the environment variable.

    ``` {#codeblock_twd_9j8_e1h}
    # cd RedisFullCheck
    # export GOPATH=`pwd`
    ```

4.  Go to the vendor directory, download the govendor file, and then grant the owner of this file the execution permission.

    ``` {#codeblock_ywx_asc_6io}
    # cd src/vendor
    # wget http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/94155/cn_zh/1556268861235/govendor
    # chmod u+x govendor
    ```

    **Note:** If you have downloaded govendor, skip this step.

5.  Run the `./govendor sync` command.
6.  After the synchronization is completed, go to the RedisFullCheck directory to compile the file.

    ``` {#codeblock_ote_lv8_42b}
    # cd .. /.. /
    # ./build.sh
    ```

7.  Run the following command to verify data:

    ``` {#codeblock_m1d_455_auh}
    # ./bin/redis-full-check -s <Source Redis address>:<Source port> -p <Source Redis password> -t <Destination Redis address>:<Destination port> -p <Destination Redis password>
    ```

    |Parameter|Description|Example|
    |---------|-----------|-------|
    |-s|The connection address and port of the source Redis instance.|`r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com:6379`|
    |-p|The password of the source Redis instance.|`SourcePwd233`|
    |-t|The connection address and port of the destination Redis instance.|`r-j6cxxxxxxxxxxxxx.redis.rds.aliyuncs.com:6379`|
    |-a|The password of the destination Redis instance.|`TargetPwd233`|

    **Note:** After the verification is completed, the comparison result is displayed on the CLI. The following result indicates that two keys are inconsistent between the source and destination Redis instances. If the number of inconsistent keys is 0, the data is consistent between the source and destination Redis instances.

    ``` {#codeblock_0u4_ypv_9w7}
    all finish successfully, totally 2 keys or fields conflict
    ```

8.  Check the SQLite3 database that stores the inconsistent keys.
    1.  Run the `sqlite3 result.db. 3` command.

        **Note:** The list of inconsistent keys is stored in result.db. 3 by default.

    2.  Run the `SELECT * FROM key;` command.

        ![](images/45982_en-US.png "View the list of inconsistent keys")

        **Note:** The SQLite3 database includes the key and field tables.

        -   The inconsistent keys are stored in the key table.
        -   Details of inconsistent data of the hash, set, zset, and list types are stored in the field table.

