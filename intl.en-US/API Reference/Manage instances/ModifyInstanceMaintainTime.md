# ModifyInstanceMaintainTime {#reference_h3w_qv2_xdb .reference}

## Description {#section_z1z_2kw_wbb .section}

This API is used to modify the maintenance time. Alibaba Cloud may perform routine maintenance for instances at the specified maintenance time.

## Request parameters {#section_fn4_gkw_wbb .section}

|Name|Type|Required|Description|
|----|----|--------|-----------|
|<Common request parameters\>|-|Yes|See [Public parameters](intl.en-US/API Reference/Common Parameters.md#section_hph_dhp_wbb).|
|Action|String|Yes|Required parameter. Value: ModifyInstanceMaintainTime.|
|InstanceId|String|Yes|Instance ID \(globally unique\)|
|MaintainStartTime|String|Yes|Maintenance start time|
|MaintainEndTime|String|Yes|Maintenance end time|

## Response parameters {#section_e4w_jkw_wbb .section}

|Name|Type|Description|
|----|----|-----------|
|<Common return parameters\>|-|See [Public return parameters](intl.en-US/API Reference/Common Parameters.md#section_rjr_zgp_wbb).|

## Request example {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com
<Common request parameters>
&Action=ModifyInstanceMaintainTime
&InstanceId=657e361a074646d5
& MaintainStartTime=02:00Z
& MaintainEndTime=06:00Z
```

## Response example {#section_hjp_tkw_wbb .section}

```

"RequestId" : "A099747A-0826-499D-9422-381C07337F73"

```

