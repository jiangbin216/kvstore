# Switch to subscription {#concept_t2l_cmg_tdb .concept}

After you purchase a Pay-As-You-Go instance, you can change its billing method to subscription as needed.

## Precautions {#section_l2s_890_fz0 .section}

-   You cannot change the billing method of a subscription instance to Pay-As-You-Go. To maximize resource usage, we recommend that you evaluate your usage model carefully before you change the billing method of an instance.
-   Within the contract period, you cannot directly release a subscription instance.
-   After the billing method of an instance is changed to subscription, the instance is immediately billed in subscription mode.
-   When you change the billing method of a Pay-As-You-Go instance to subscription, the system generates a purchase order. The changed billing method takes effect only after you pay for this order. If you do not pay or fail to pay, an unpaid order is listed on the [order management](https://billing.console.aliyun.com/?#/order/list/) page of your Alibaba Cloud account. In this case, you cannot purchase any instances or change the billing method of any instances.

    **Note:** 

    -   If you have an unpaid order for changing the billing method of a Pay-As-You-Go instance to subscription and you upgrade the configuration of this Pay-As-You-Go instance, the amount of the unpaid order is insufficient to cover the changed billing method due to the changed instance components. In this case, the system forbids you to pay for this order. You must void this unpaid order and change the billing method of the instance again.
    -   If you want to cancel an unpaid order, you can void it on the [order management](https://billing.console.aliyun.com/?#/order/list/) page of the console.

## Prerequisites {#section_y4z_wlg_vdb .section}

-   The billing method of an instance is Pay-As-You-Go. The instance is in the **Running** status.

    **Note:** Before you pay for a purchase order for changing the billing method of a Pay-As-You-Go instance to subscription, if the status of this instance changes \(for example, to **Locked**\), you may fail to pay for this order. You can continue to pay only after the instance status changes to Running.

-   The instance has no unpaid order for changing the billing method.

## Procedure {#section_wvf_xlg_vdb .section}

1.  Log on to the [ApsaraDB for Redis console](https://kvstore.console.aliyun.com/).
2.  In the upper-left corner of the top navigation bar, select the region where the target instance is located.
3.  On the Instance List page, find the target instance and click **Switch to Subscription** in the Action column.
4.  Adjust the slider of **Duration** to select a subscription period.
5.  Click **Confirm** and pay for the generated order as prompted.

## Related API operations {#section_fln_dt4_tgb .section}

|API|Description|
|---|-----------|
|[TransformToPrePaid](../../../../intl.en-US/API Reference/Lifecycle management/TransformToPrePaid.md#)|You can call this operation to change the billing method of an ApsaraDB for Redis instance from Pay-As-You-Go to subscription.|

