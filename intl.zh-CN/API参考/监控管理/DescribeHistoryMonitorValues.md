# DescribeHistoryMonitorValues {#doc_api_R-kvstore_DescribeHistoryMonitorValues .reference}

调用DescribeHistoryMonitorValues查看实例的历史监控信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=DescribeHistoryMonitorValues)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeHistoryMonitorValues|系统规定参数，取值：DescribeHistoryMonitorValues。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|目标实例的ID。

 |
|StartTime|String|是|2018-10-18T12:00:00Z|历史监控开始时间点；采用ISO8601表示法，并使用UTC时间。格式为：YYYY-MM-DDThh:mm:ssZ。

 |
|EndTime|String|是|2018-10-19T12:00:00Z|历史监控结束时间点；采用ISO8601表示法，并使用UTC时间。格式为：YYYY-MM-DDThh:mm:ssZ。结束时间必须晚于开始时间。

 |
|IntervalForHistory|String|是|01m|历史监控数据间隔，单位m（分钟），唯一值`01m`。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |
|MonitorKeys|String|否|hscan|监控项。可调用[DescribeMonitorItems](~~61106~~)查询。

 |
|NodeId|String|否|r-bp1xxxxxxxxxxxxx-db-0\#6xxxxx5|传入集群实例中特定子节点的ID查询该节点的监控信息。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|MonitorHistory|String|\{"2018-07-09T12:00:13Z": \{"quotaMemory": 1073741824,"UsedMemory": 5823152\},"2018-07-09T12:13:15Z": \{"quotaMemory": 1073741824,"UsedMemory": 5823152\},"2018-07-09T12:14:15Z": \{"quotaMemory": 1073741824,"UsedMemory": 5823152\}\}|以JSON格式返回的监控信息。

 **说明：** 为了提高数据传输效率，只有非0的监控数据才会返回，其余未显示的监控数据均为默认值0。

 |
|RequestId|String|F0997EE8-F4C2-4503-9168-85177ED78C70|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=DescribeHistoryMonitorValues
&InstanceId=r-j6cxxxxxxxxxx3d4
&StartTime=2018-10-18T12:00:00Z
&EndTime=2018-10-19T12:00:00Z
&IntervalForHistory=01m
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeHistoryMonitorValuesResponse>
 <monitorHistory>
   <2018-07-09T12:00:13Z>
     <quotaMemory>1073741824</quotaMemory>
     <UsedMemory>5823152</UsedMemory>
   </2018-07-09T12:00:13Z>
   <2018-07-09T12:13:15Z>
     <quotaMemory>1073741824</quotaMemory>
     <UsedMemory>5823152</UsedMemory>
   </2018-07-09T12:13:15Z>
   <2018-07-09T12:14:15Z>
     <quotaMemory>1073741824</quotaMemory>
     <UsedMemory>5823152</UsedMemory>
   </2018-07-09T12:14:15Z>
 </monitorHistory>
 <requestId>F0997EE8-F4C2-4503-9168-85177ED78C70</requestId>
</DescribeHistoryMonitorValuesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"monitorHistory":{
		"2018-07-09T12:13:15Z":{
			"quotaMemory":1073741824,
			"UsedMemory":5823152
		},
		"2018-07-09T12:14:15Z":{
			"quotaMemory":1073741824,
			"UsedMemory":5823152
		},
		"2018-07-09T12:00:13Z":{
			"quotaMemory":1073741824,
			"UsedMemory":5823152
		}
	},
	"requestId":"F0997EE8-F4C2-4503-9168-85177ED78C70"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|The Specified parameter "StartTime" is not valid.|开始时间验证失败，时间格式应该为gmt时间例如，2011-06-11T16:00Z|
|400|InvalidEndTime.Malformed|The Specified parameter "EndTime" is not valid.|结束时间验证失败，时间格式应该为gmt时间例如，2011-06-11T16:00Z|

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

