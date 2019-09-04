# Can an ECS instance in a VPC connect to an ApsaraDB for Redis instance in a classic network? {#concept_stg_4zz_xdb .concept}

A virtual private cloud \(VPC\) and a classic network are two subnets. They cannot interconnect with each other over an internal network. You can solve this issue in the following ways:

-   If you allow changing the network type of the ApsaraDB for Redis instance, you can switch the ApsaraDB for Redis instance to the VPC where the ECS instance is located. For more information, see [Switch to VPC](../../../../reseller.en-US/User Guide/Manage instances/Switch to VPC.md#). However, you cannot switch the ApsaraDB for Redis instance from the VPC to a classic network.

    **Note:** 

    When you change the network type, if no switch is available, you can create a switch in the VPC. The switch stays in the same zone as the ApsaraDB for Redis instance. Afterward, switch to the VPC. For more information about how to create a switch, see [Create a VSwitch](../../../../reseller.en-US/VPCs and VSwitches/VSwitch management/Create a VSwitch.md#).

-   If you do not allow changing the network type of the ApsaraDB for Redis instance, you have to purchase an ECS instance in a classic network. Because the ECS instance does not support switching from a VPC to a classic network.


