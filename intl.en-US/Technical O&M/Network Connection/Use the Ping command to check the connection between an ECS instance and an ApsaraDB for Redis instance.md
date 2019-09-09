# Use the Ping command to check the connection between an ECS instance and an ApsaraDB for Redis instance {#concept_bzb_hcl_5gb .concept}

Check the connection between an ECS instance and an ApsaraDB for Redis instance after you create the ApsaraDB for Redis instance or when the ECS instance cannot reach the ApsaraDB for Redis instance in running status. You can run the Ping command in the command-line interface \(CLI\) on the ECS instance to check whether the ECS instance can reach the ApsaraDB for Redis instance.

## Procedure {#section_rhs_3jl_5gb .section}

1.  Check the [connection address\(endpoint\)](../../../../reseller.en-US/User Guide/Connection management/View endpoints.md#) of the ApsaraDB for Redis instance.
2.  Log on to the ECS instance and run the following command in the CLI:

    ``` {#codeblock_bqp_q6z_yi9}
    ping <host>
    ```

    **Note:** 

    -   In this command, `<host>` specifies the connection address that you obtained in Step 1.
    -   You can run this command in both Windows and Linux operating systems.
3.  Check the test result.
    -   In Windows, the system shows the test result after running the Ping command four times.

        **Note:** To continuously check the connection, run the `ping <host> -t` command.

    -   The Linux system continuously sends Ping messages when running the Ping command. You can press CTRL and C on the keyboard to stop running the command and collect statistics, as shown in the following figure.

        ![Reach the ApsaraDB for Redis instance from a Linux server by using Ping messages](images/38973_en-US.png "Run the Ping command on a Linux server")


## Result analysis {#section_xsp_z4m_vgb .section}

-   If all responses indicate successful connections, the connection is normal.
-   If no response indicates a successful connection, the connection is abnormal. We recommend that you follow the steps in [Troubleshooting for connection issues in ApsaraDB for Redis](../../../../reseller.en-US/FAQs/Troubleshooting for connection issues in ApsaraDB for Redis.md#) and check settings of the ECS instance and the ApsaraDB for Redis instance, such as whitelists and security groups. Also, you can perform troubleshooting for issues caused by DNS resolution.

