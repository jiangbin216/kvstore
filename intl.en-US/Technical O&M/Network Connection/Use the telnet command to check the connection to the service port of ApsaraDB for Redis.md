# Use the telnet command to check the connection to the service port of ApsaraDB for Redis {#concept_ygd_gpt_vgb .concept}

During the troubleshooting for connection issues in ApsaraDB for Redis, you must check the connection to the service port.

## Prerequisites {#section_kx1_wst_vgb .section}

You have installed the telnet client for Linux or enabled the telnet client for Windows on the ECS instance.

## Background {#section_anr_5pt_vgb .section}

A connection issue occurs in the ApsaraDB for Redis service, but the ECS instance can reach the ApsaraDB for Redis instance by using the [Ping](reseller.en-US/Technical O&M/Network Connection/Use the Ping command to check the connection between an ECS instance and an ApsaraDB for Redis instance.md#) command. In this case, you need to use the telnet command to check whether the service port of ApsaraDB for Redis is available.

## Procedure {#section_tjd_15t_vgb .section}

1.  [Check the connection address of the ApsaraDB for Redis instance](../../../../reseller.en-US/User Guide/Connection management/View endpoints.md#).
2.  Log on to the ECS instance and run the following command in the command-line interface \(CLI\):

    ``` {#codeblock_5yz_wd9_bkl}
    telnet <host> 6379
    ```

    **Note:** 

    -   In this command, `<host>` specifies the connection address that you obtained in Step 1.
    -   The value 6379 is the default port number for ApsaraDB for Redis.
    -   You can run this command in both Windows and Linux operating systems.
     ![](images/39034_en-US.png "Run the telnet command in Linux")

     ![](images/39016_en-US.png "Run the telnet command in Windows")

3.  Check the test result. The following examples show the results of running the command in Linux and Windows.
    -   The telnet-based connection is successful.

         ![](images/39036_en-US.png "Successful telnet-based connection in Linux")

        ![Successful telnet-based connection in Windows](images/39017_en-US.png "Successful telnet-based connection in Windows")

    -   The telnet-based connection is failed.

        ![Failed telnet-based connection to ApsaraDB for Redis in Linux](images/39045_en-US.png "Failed telnet-based connection in Linux")

        ![Failed telnet-based connection to ApsaraDB for Redis in Windows](images/39044_en-US.png "Failed telnet-based connection in Windows")


## Result analysis {#section_svh_tq5_vgb .section}

-   If a connection issue occurs in the ApsaraDB for Redis service, but the ECS instance can reach the ApsaraDB for Redis instance by using a telnet command, the ECS instance is normally connected to the ApsaraDB for Redis instance. You need to check other causes, such as clients, service code, and Redis service blocking due to service environment. For more information, see [Troubleshooting for connection issues in ApsaraDB for Redis](../../../../reseller.en-US/FAQs/Troubleshooting for connection issues in ApsaraDB for Redis.md#).
-   If the telnet-based connection fails, but the ECS instance can reach the ApsaraDB for Redis instance by using the [Ping](reseller.en-US/Technical O&M/Network Connection/Use the Ping command to check the connection between an ECS instance and an ApsaraDB for Redis instance.md#) command, the ECS instance probably has abnormal behavior and some services have been disabled. For example, the ECS instance attacks Port 6379 of the ApsaraDB for Redis instance due to malicious programs. In this case, we recommend that you monitor the data on the ECS instance to locate and handle abnormal traffic, or submit a ticket to request technical support.
-   If the telnet-based connection fails and the system generates the error `Name or service not known`, the connection address may be incorrect or the Domain Name System \(DNS\) resolution has an exception. Make sure that the connection address is correct. Afterward, follow the steps in [Solve connection issues caused by failed DNS resolution](reseller.en-US/Technical O&M/Network Connection/Solve connection issues caused by failed DNS resolution.md#).

