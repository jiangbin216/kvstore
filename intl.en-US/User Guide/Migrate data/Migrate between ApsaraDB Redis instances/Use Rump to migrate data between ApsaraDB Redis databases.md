# Use Rump to migrate data between ApsaraDB Redis databases {#task_njf_rfw_mfb .task}

You can use Rump to migrate data between databases within the same ApsaraDB Redis instance or between different ApsaraDB Redis instances.

-   You have created a Linux-based Elastic Compute Service \(ECS\) instance in the VPC where the target ApsaraDB for Redis instance resides.
-   You have downloaded [Rump](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/94155/jp_ja/1539856046329/rump) in the ECS instance you created. You have change the file type of Rump to an executable file.

You will encounter the following problems when migrating Redis data from cloud service providers:

-   The data acquisition commands such as slaveof and bgsave are not supported.
-   The keys command is likely to cause congestion on the server and affect operating services.

Migration mechanism of Rump

Rump executes a single scan command to acquire multiple key lists from the source ApsaraDB for Redis instance. Rump retrieves the key content with the dump command, and obtains the expiration time of the keys through the pttl command. Then, Rump uses the restore command to synchronize the keys to the target ApsaraDB for Redis instance in pipeline mode.

Benefits:

-   The keys command is replaced with the scan command to avoid consequential congestion on the server.
-   Data of any type can be synchronized.
-   No temporary files are used.
-   Channels with buffer are used to improve performance of the source server.
-   The pipeline mode is adopted to save network bandwidth.

1.  Run the following command in the ECS instance to synchronize data: 

    ```
    rump -from source_addr -fromPwd source_pwd -to dest_addr -toPwd dest_pwd [-size size] [-replace]
    ```

    |Parameter|Description|
    |---------|-----------|
    |source\_addr|The address of the source ApsaraDB for Redis instance, in format of `redis://host:port/db`. host and port are required parameters while db is an optional one. If db is not specified, the value 0 is used by default.|
    |source\_pwd|The password of the source ApsaraDB for Redis instance.|
    |dest\_addr|The address of the target ApsaraDB for Redis instance, in the same format as source\_addr.|
    |dest\_pwd|The password of the target ApsaraDB for Redis instance.|
    |size|The number of keys that are synchronized at a time. Default value: 10.|
    |-replace|Indicates whether to overwrite an existing key if it is the same as a new key. If this parameter is specified, the existing key is overwritten. If this parameter is not specified, the existing key is not overwritten and an error message is displayed.|


-   **Example 1: Import the data from db0 to db1 within the same ApsaraDB for Redis instance.**

    ```
    rump -from redis://r-123456789.redis.rds.aliyuncs.com:6379/0 -fromPwd from_pass -to redis://r-123456789.redis.rds.aliyuncs.com:6379/1 -toPwd to_pass -size 100 
    
    
    ```

-   **Example 2: Import the data from db0 of ApsaraDB for Redis instance A to db1 of ApsaraDB for Redis instance B.**

    ```
    rump -from redis://r-123456789.redis.rds.aliyuncs.com:6379/0 -fromPwd from_pass -to redis://r-999999999.redis.rds.aliyuncs.com:6379/1 -toPwd to_pass -size 100 
    
    
    ```


