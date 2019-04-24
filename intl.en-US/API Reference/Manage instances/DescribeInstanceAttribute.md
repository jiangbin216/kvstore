# DescribeInstanceAttribute {#reference_nyk_w52_xdb .reference}

## Description {#section_z1z_2kw_wbb .section}

This API is used to query details of an instance.

## Request parameters {#section_fn4_gkw_wbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|For more information, see [Public parameters](intl.en-US/API Reference/Common Parameters.md#section_hph_dhp_wbb).|
|Action|String|Yes|Required parameter. Value: DescribeInstanceAttribute.|
|InstanceId|String|Yes|Instance ID \(globally unique\)|

## Response parameters {#section_e4w_jkw_wbb .section}

|Name|Type|Description|
|----|----|-----------|
|Instances|List|Array composed of DBInstanceAttributes|

## DBInstanceAttribute parameter structure {#section_c14_bpw_wbb .section}

|Name|Type|Description|
|----|----|-----------|
|InstanceId|String|Instance ID \(globally unique\)|
|InstanceName|String|Instance name|
|Capacity|Long|Capacity of the applied ApsaraDB for Redis instance. Unit: MB.|
|InstanceClass|String|Instance type|
|Bandwidth|Long|Instance bandwidth limit. Unit: Mbit/s.|
|Connections|Long|Instance connection quantity limit. Unit: count.|
|ConnectionDomain|String|Connection domain of the ApsaraDB for Redis instance \(only Intranet access supported\)|
|Port|Int|ApsaraDB for Redis connection port|
|RegionId|String|Region of the applied ApsaraDB for Redis instance. For more information, see [DescribeRegions](intl.en-US//DescribeRegions.md#).|
|ZoneId|String|Lower-level zone ID of the RegionId. For more information, see [DescribeRegions](intl.en-US//DescribeRegions.md#).|
|InstanceStatus|String| Instance status:

 -   Normal
-   Creating
-   Changing
-   Inactive

 |
|ChargeType|String|Billing method. Supported values: PrePaid and PostPaid.|
|CreateTime|String|Instance creation time. The time format follows the ISO8601 notation, and the UTC  time is used in the format of `YYYY-MM-DDThh:mm:ssZ`.|
|EndTime|String|Expiration time for a pre-paid instance. The time format follows the ISO8601 notation, and the UTC time is used in the format of `YYYY-MM-DDThh:mm:ssZ`.|
|NetworkType|String|Network type. Supported values: CLASSIC and VPC.|
|VpcId|String|VPC ID|
|VSwitchId|String|VSwitch ID|
|PrivateIpAddress|String|Private IP address|
|MaintainStartTime|String|Maintenance start time|
|MaintainEndTime|String|Maintenance end time|
|SecurityIPList|String|IP address whitelist|
|AvailabilityValue|String|Availability metrics of the current month|

**Note:** In consideration of the historical compatibility, some returned fields \(such as Config and Region\) of the function are not mentioned in this document. Alibaba Cloud will delete these fields gradually in the future. In this case, do not rely on the returned fields not involved in this document when calling the APls.

## Request example {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com、
? <Common request parameters>
&Action=DescribeInstanceAttribute
&InstanceId=736538d0a6894665
```

## Response example {#section_hjp_tkw_wbb .section}

```
{
{
    "Instances" : {
        " DBInstanceAttribute " : [{
                "Bandwidth" : 128,
                "Capacity" : 512,
                "ConnectionDomain" : "de5d88e34d004211.m.cnhzalicm10pub001.r-kvstore.aliyuncs.com.com",
                "Connections" : 300,
                "ZoneId" : "cn-qingdao-b",
                "InstanceId" : "de5d88e34d004211",
                "InstanceName" : "wl123456",
                "InstanceStatus" : "Available",
                 "InstanceClass" : "redis.master.mid.default",
                "Port" : 11211,
                "QPS" : 4500,
                "RegionId" : "cn-qingdao",
                 "ChargType"："PostPaid",
                  "NetworkType":"ClASSSIC"
                "MaintainStartTime"："02：00Z",
                 "MaintainEndTime"："06：00Z",
                 "SecurityIPList": "192.168.0.1"，
                  "AvailabilityValue":"100%"
        }]
  }
"RequestId" : "283746AF-82B3-4BFF-88CC-BF34CDE2732”
}
```

