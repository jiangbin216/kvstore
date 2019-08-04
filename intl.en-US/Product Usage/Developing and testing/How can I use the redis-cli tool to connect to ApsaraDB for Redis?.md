# How can I use the redis-cli tool to connect to ApsaraDB for Redis? {#concept_zbx_bz5_ydb .concept}

To use the redis-cli tool to connect to ApsaraDB for Redis, run the following command:

``` {#codeblock_oc5_q47_s3e}
*redis-cli -h <Connection address of the target instance\> -a <Instance ID\>:<Password\>*
```

**Note:** An ECS instance and an ApsaraDB for Redis instance can interconnect with each other only when they run on the same node. Because ApsaraDB for Redis only supports connections over an internal network. You cannot connect to the service over a public network or from a server on another node in a public network.

If the issue persists, submit a ticket to [request technical support](https://workorder-intl.console.aliyun.com/#/ticket/add?productId=1226).

