# DescribeDBInstanceNetInfo {#doc_api_R-kvstore_DescribeDBInstanceNetInfo .reference}

调用DescribeDBInstanceNetInfo查看Redis实例的网络信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=DescribeDBInstanceNetInfo)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDBInstanceNetInfo|系统规定参数，取值：DescribeDBInstanceNetInfo。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|目标实例的ID。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|InstanceNetworkType|String|CLASSIC|网络类型：

 -   CLASSIC（经典网络）
-   VPC（专有网络）

 |
|NetInfoItems| | |网络信息的集合。

 |
|└ConnectionString|String|r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com|实例的连接地址。

 |
|└DBInstanceNetType|String|1|该网络信息所属的网络类型：

 -   0（公网）
-   1（经典网络）
-   2（VPC网络）

 |
|└IPAddress|String|xxx.xxx.xxx.201|IP地址。

 |
|└IPType|String|Inner|IP地址的网络类型：

 -   Public（公网）
-   Inner（经典网络）
-   Private（VPC网络）

 |
|└Port|String|6379|Redis服务端口。

 |
|└Upgradeable|String|0|经典网络连接地址的过期时间，即剩余有效时间，以秒为单位。0表示不会过期。

 |
|└VPCId|String|vpc-bp1cxxxxxxxxxxxxxxxxx|实例所属的专有网络（VPC）的ID。

 |
|└VPCInstanceId|String|r-bp1xxxxxxxxxxxxx|实例ID，仅在DBInstanceNetType为2（VPC网络）的网络信息中返回。

 |
|└VSwitchId|String|vsw-4gxxxxxxxxxxxxxxxxxxx|虚拟交换机的ID。

 |
|RequestId|String|314C4FB3-4256-424F-9AD9-1A6B3444160A|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=DescribeDBInstanceNetInfo
&InstanceId=r-bp1xxxxxxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeDBInstanceNetInfoResponse>
  <RequestId>E4866AEC-CE71-4156-8BAA-A078D5B8EF3F</RequestId>
  <InstanceNetworkType>VPC</InstanceNetworkType>
  <NetInfoItems>
    <InstanceNetInfo>
      <DBInstanceNetType>1</DBInstanceNetType>
      <Port>6379</Port>
      <ConnectionString>r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com</ConnectionString>
      <VPCInstanceId/>
      <VPCId/>
      <IPAddress>xxx.xxx.xxx.201</IPAddress>
      <IPType>Inner</IPType>
      <Upgradeable>0</Upgradeable>
      <ExpiredTime>5183779</ExpiredTime>
    </InstanceNetInfo>
    <InstanceNetInfo>
      <DBInstanceNetType>0</DBInstanceNetType>
      <Port>6379</Port>
      <ConnectionString>r-bp1xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com</ConnectionString>
      <VPCInstanceId/>
      <VPCId/>
      <IPAddress>xxx.xxx.xxx.146</IPAddress>
      <IPType>Public</IPType>
      <Upgradeable>0</Upgradeable>
    </InstanceNetInfo>
    <InstanceNetInfo>
      <DBInstanceNetType>2</DBInstanceNetType>
      <Port>6379</Port>
      <ConnectionString>r-bp1xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com</ConnectionString>
      <VPCInstanceId>r-bp1xxxxxxxxxxxxx</VPCInstanceId>
      <VPCId>vpc-bp1cxxxxxxxxxxxxxxxxx</VPCId>
      <IPAddress>xxx.xxx.xxx.245</IPAddress>
      <IPType>Private</IPType>
      <Upgradeable>0</Upgradeable>
    </InstanceNetInfo>
  </NetInfoItems>
</DescribeDBInstanceNetInfoResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E4866AEC-CE71-4156-8BAA-A078D5B8EF3F",
	"InstanceNetworkType":"VPC",
	"NetInfoItems":{
		"InstanceNetInfo":[
			{
				"ConnectionString":"r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com",
				"Port":"6379",
				"DBInstanceNetType":"1",
				"VPCId":"",
				"VPCInstanceId":"",
				"IPAddress":"xxx.xxx.xxx.201",
				"IPType":"Inner",
				"Upgradeable":"0",
				"ExpiredTime":"5183779"
			},
			{
				"ConnectionString":"r-bp1xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com",
				"Port":"6379",
				"DBInstanceNetType":"0",
				"VPCId":"",
				"VPCInstanceId":"",
				"IPAddress":"xxx.xxx.xxx.146",
				"IPType":"Public",
				"Upgradeable":"0"
			},
			{
				"ConnectionString":"r-bp1xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com",
				"Port":"6379",
				"DBInstanceNetType":"2",
				"VPCId":"vpc-bp1cxxxxxxxxxxxxxxxxx",
				"VPCInstanceId":"r-bp1xxxxxxxxxxxxx",
				"IPAddress":"xxx.xxx.xxx.245",
				"IPType":"Private",
				"Upgradeable":"0"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|The Specified parameter StartTime is not valid.|开始时间验证失败，时间格式应该为gmt时间例如2011-06-11T16:00Z|
|400|InvalidEndTime.Malformed|The Specified parameter EndTime is not valid.|结束时间验证失败，时间格式应该为gmt时间例如2011-06-11T16:00Z|

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

