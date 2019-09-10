# Disable high-risk commands {#task_uzq_tgk_5gb .task}

You can modify a parameter of an ApsaraDB for Redis instance in the console to disable some commands that may affect service performance or harm data security.

Allowing the use of all commands may cause many issues. Some Redis commands clear a large amount or even all of the data, such as FLUSHALL and FLUSHDB. Improper use of commands such as KEYS and HGETALL blocks single-thread Redis services and reduce the Redis service performance. To ensure stable and efficient business operation, you can disable specific commands to reduce business risks.

1.  Log on to the [ApsaraDB for Redis console](https://partners-intl.console.aliyun.com/#/kvstore).
2.  In the upper-left corner of the top navigation bar, select the region where the target instance is located.
3.  On the **Instance List** page, click the target instance ID or **Manage** in the Action column for the target instance.
4.  On the Instance Information page, click **System Parameters** in the left-side navigation pane.
5.  On the System Parameters page, locate the \#no\_loose\_disabled-commands parameter and click **Modify** in the Action column. 

    ![Disable specific Redis commands](images/38847_en-US.png "Disable specific Redis commands in parameter settings")

6.  In the dialog box that appears, set the parameter to the commands to be disabled, and then click **OK**. 

    ![Set the Redis commands to be disabled](images/38850_en-US.png "Set the commands to be disabled")

    **Note:** 

    -   The parameter value can contain only lowercase letters. Separate multiple commands with commas \(,\).
    -   Commands that can be disabled include FLUSHALL, FLUSHDB, KEYS, HGETALL, EVAL, EVALSHA, and SCRIPT.

