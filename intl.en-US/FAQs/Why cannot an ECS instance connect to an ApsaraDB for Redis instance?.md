# Why cannot an ECS instance connect to an ApsaraDB for Redis instance? {#concept_m2x_pbz_xdb .concept}

## Connect through the Alibaba Cloud intranet {#section_05f_los_zaw .section}

Both instances can interconnect with each other over the Alibaba only when:

-   The ECS instance and the ApsaraDB for Redis instance reside in the same region.
-   The ECS instance and the ApsaraDB for Redis instance run in the same type of network, a classic network or a virtual private cloud \(VPC\).
-   A whitelist of the ApsaraDB for Redis instance includes the internal IP address of the ECS instance.

The ECS instance cannot directly connect to the ApsaraDB for Redis instance over an internal network in the following conditions:

-   The ECS instance and the ApsaraDB for Redis instance run in different VPCs in different regions. To connect the ECS instance and the ApsaraDB for Redis instance from different regions, you have to use the Express Connect service and establish a connection across VPCs over an internal network. For more information, see [Interconnect two VPCs under different accounts](../../../../reseller.en-US/Peering connections/Interconnect two VPCs under different accounts.md#).
-   The ECS instance and the ApsaraDB for Redis instance run in different types of networks. You can solve this issue in the following ways:
    -   If permitted, switch the network type to the VPC. For more information, see [Switch to VPC](../../../../reseller.en-US/User Guide/Manage instances/Switch to VPC.md#) or [Migration overview](../../../../reseller.en-US/Best practices/Migrate from the classic network to VPC/Migration overview.md#).
    -   If your business does not allow switching instances to VPC, you have to purchase the ECS instance and the ApsaraDB for Redis instance that run in a classic network and in the same region.

## Connect through the Internet {#section_1fu_fuf_8a8 .section}

To connect an ApsaraDB for Redis instance through the Internet, you must apply a public endpoint for the Redis instance first, see [Through the Internet](../../../../reseller.en-US/Quick Start/Step 3: Connect to the instance/Through the Internet.md#), then connect to the Redis instance with the public endpoint.

