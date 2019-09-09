# Solve connection issues caused by failed DNS resolution {#concept_bkb_qbn_qgb .concept}

When you connect to the ApsaraDB for Redis instance by using the connection address, the ECS instance fails to resolve the connection address due to a DNS \(Domain Name System\) service issue. As a result, the ECS instance is disconnected from the ApsaraDB for Redis instance. You can try to solve this issue by following the steps in this topic.

## Background {#section_ec3_wbn_qgb .section}

Various reasons may lead to connection issues between the ECS instance and the ApsaraDB for Redis instance. Failed DNS resolution is a common cause. When the system generates the error such as `UnknownHostException` or `failed to connect: r-***************.redis.rds.aliyuncs.com could not be resolved`, the host name is unknown or the resolution of the connection address is failed. Check whether the domain name and DNS server settings are correct, and refresh the DNS cache.

**Note:** The following example describes the steps in the Linux operating system.

## Procedure {#section_x2c_hdn_qgb .section}

1.  Check whether the [endpoint\(connection address\)](../../../../reseller.en-US/User Guide/Connection management/View endpoints.md#) in the service code of the ApsaraDB for Redis instance is correct.
2.  Run the `# cat /etc/resolv.conf` command to check whether you have specified the correct IP address of the DNS server in the /etc/resolv.conf file on the ECS instance.

    ![Check the IP address of the DNS server](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/123243/156802039138585_en-US.png)

    **Note:** 

    -   If you have not specified the DNS server, run the `# vi /etc/resolv.conf` command to edit the /etc/resolv.conf file. Add the IP address of the DNS server in the format as shown in the preceding figure. Afterward, press ECS on the keyboard, type :wq, and then press ENTER to save the modification.
    -   We recommend that you use the default DNS server on the ECS instance or use another secure and stable DNS server.
3.  Based on your DNS service, clear the DNS cache in any of the following ways:
    -   Clear the DNS cache of Name Service Cache Daemon \(nscd\):

        ``` {#codeblock_mmx_igt_7kr}
        # service nscd restart
        ```

        Or run the following command:

        ``` {#codeblock_nrw_ysx_2g9}
        # service nscd reload
        ```

    -   Clear the DNS cache of dnsmasq:

        ``` {#codeblock_5k3_oyn_e3w}
        # service dnsmasq restart
        ```

    -   Clear the DNS cache on the Berkely Internet Name Domain \(BIND\) server:

        ``` {#codeblock_l3f_drm_opk}
        # /etc/init.d/named restart
        ```

        Or run the following command:

        ``` {#codeblock_ita_io2_v0w}
        # rndc restart
        ```


**Note:** If the issue persists, add the mapping between the domain name and the IP address of the ApsaraDB for Redis instance to the /etc/hosts file to resolve the domain name correctly. Afterward, follow steps in [Troubleshooting for connection issues in ApsaraDB for Redis](../../../../reseller.en-US/FAQs/Troubleshooting for connection issues in ApsaraDB for Redis.md#) and try to solve connection issues due to other causes. For more information about how to edit the hosts file, see Step 2 and the following figure. This method is only a temporary solution. If the IP address of the ApsaraDB for Redis instance changes, this solution is invalid.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/123243/156802039138636_en-US.png)

