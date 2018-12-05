# Use the redis-port tool to migrate data between ApsaraDB Redis instances of different accounts {#task_zgn_tk1_hfb .task}

You can use the redis-port tool to migrate data from one ApsaraDB Redis instance to another instance under a different Alibaba Cloud account.

-   You have created a Linux-based Elastic Compute Service \(ECS\) instance in the VPC where the target ApsaraDB for Redis instance resides.
-   You have downloaded the [redis-port](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/85829/cn_zh/1533199526614/redis-port%282%29?spm=a2c4g.11186623.2.10.1b5447ceE6Wtwt) tool in the ECS instance you created.
-   You have run the chmod u+x redis-port command to change redis-port into an executable file.
-   You have run the mkdir logs command in the directory where redis-port is located.

1.  Log on to the [ApsaraDB for Redis console](https://kvstorenext.console.aliyun.com). 
2.   On the Instance List page, locate the source ApsaraDB for Redis instance. Then click the instance ID, or click the vertical dots in the Action column and choose **Manage** from the shortcut menu. 
3.   Click **Backup and Recovery** in the left-side navigation pane. 
4.  Locate the target backup file in the backup file list, and click **Download** in the **Action** column. 

    **Note:** To create a backup file instantly, click Create Backup in the upper-right corner of the **Backup and Recovery** page. In the Backup Instance message box that appears, click **Confirm**.

5.   In the displayed Download Backup File dialog box, click **Get URL for Intranet**. 
6.  In the ECS instance, download the backup file from the address copied in the previous step. 

    **Note:** For an ApsaraDB for Redis instance of the cluster type, multiple backup files will be generated based on the number of sub-nodes, and you need to download all of the files.

7.  Run the following command to import all the backup files to the target database: ./redis-port restore -i backup file name -t domain name or IP address of the target database:port number --auth='password of the target database' 

If restore: rdb done appears, data import succeeds. Migration is completed.

