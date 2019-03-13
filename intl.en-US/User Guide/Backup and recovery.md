# Backup and recovery {#concept_up2_fmg_tdb .concept}

As an increasing number of businesses use ApsaraDB for Redis as the ultimate persistent storage engine, users have posed higher data reliability requirements. The ApsaraDB for Redis backup and recovery solution enables comprehensive data reliability upgrade.

## Automatic backup \(backup policy setting\) { .section}

**Background**

As more and more applications use ApsaraDB for Redis for persistent storage, conventional backup mechanisms are required to quickly recover data in the event of misoperation. Alibaba Cloud runs RDB snapshot backup on slave nodes to protect the performance of your instance during the backup process. Alibaba Cloud also provides convenient console operations, so you can customize the backup settings.

**Procedure**

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Select **Backup and Recovery** in the left-side navigation pane .
4.  Click **Backup Settings**.
5.  Click **Edit** to customize the automatic backup cycles and times.

    **Note:** By default, backup data is retained for 7 days. This setting cannot be modified.

6.  Click **OK** to complete automatic backup setting.

## Manual backup \(instant backup\) { .section}

In addition to the general backup settings, you can initiate a manual backup request on the console at any time.

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Select **Backup and Recovery** in the left-side navigation pane .
4.  Click **Create Backup** in the upper-right corner.
5.  Click OK to instantly back up the instance.

    **Note:** On the Backup Data page, you can select time ranges to query historical backup data. By default, backup data is retained for 7 days, so you can query historical backup data from the last 7 days.


## Backup archiving { .section}

**Background**

Due to industry regulatory or corporate policy requirements, you may need to regularly archive Redis data backups. ApsaraDB for Redis provides a backup archiving function at no charge currently and saves automatic and manual backup files to OSS. Now, Alibaba Cloud stores your backup archives on OSS for 7 days at no charge. After 7 days, the files are automatically deleted.

If you must retain these archives for a longer period of time, you can copy the link on the console and manually download the database backup files for local storage.

**Procedure**

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Select **Backup and Recovery** in the left-side navigation pane .
4.  On the backup data page, select the backup data to be archived and click **Download**.

## Data recovery { .section}

The data recovery function minimizes the damage caused by database misoperations. Now, ApsaraDB for Redis supports data recovery from backups.

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Select **Backup and Recovery** in the left-side navigation pane .
4.  Click the Backup Data tab on the Backup and Recovery page.
5.  Select the time range for recovery and click **Search**. Then select the target backup file and click **Recover Data**.
6.  In the Data Recovery window, click **OK** to recover the data directly to the original instance. Alternatively, you can choose **Clone Instance** to recover the backup data to a new instance. After verifying that the recovered data is correct, you can recover the data to the original instance.

    **Note:** As the data recovery operation is highly risky, we suggest using the clone instance method if time permits. This method creates a Pay-As-You-Go instance based on the backup data set to be recovered. After verifying that the data is correct, you can recover the data to the original instance.


## Clone instance { .section}

**Background**

During routine maintenance projects, O&M engineers often need to quickly deploy a new application. When application deployment is relatively simple, a new instance can be conveniently created based on an ECS image file. At the database level, however, deployment is more complex. O&M engineers must purchase or install a new database and then initialize relevant database scripts \(to create tables, triggers, and views\). In such a scenario, many trivial operations must be performed and the error rate is relatively high. Especially in the gaming industry with fast service activation, the rapid deployment of new applications often needs to be repeated many times each day.

To address this pain point, ApsaraDB for Redis develops the clone instance function, enabling you to clone a new subscribed instance or Pay-As-You-Go instance from backup files quickly. Then you can perform complex operations of database development and deployment with a single click on a graphic interface, significantly improving productivity.

**Procedure**

1.  Log on to the [Redis console](https://kvstore.console.aliyun.com/) and find the target instance.
2.  Click the instance ID or **Manage** to go to the Instance Information page.
3.  Select **Backup and Recovery** in the left-side navigation pane .
4.  On the Backup Data page, select the expected backup data set and click **Clone Instance.**

