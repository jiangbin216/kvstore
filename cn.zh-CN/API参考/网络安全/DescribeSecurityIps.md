# DescribeSecurityIps {#doc_api_R-kvstore_DescribeSecurityIps .reference}

调用DescribeSecurityIps查询允许访问实例的IP名单。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=DescribeSecurityIps)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeSecurityIps|系统规定参数，取值：DescribeSecurityIps。

 |
|InstanceId|String|是|r-j6cxxxxxxxxxx3d4|目标实例的ID。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|SecurityIpGroups| | |实例的IP白名单信息。

 |
|└SecurityIpGroupAttribute|String|""|默认为空。用于区分不同的属性值，控制台将不显示该值为hidden的白名单分组。

 |
|└SecurityIpGroupName|String|default|IP白名单分组的名称。

 |
|└SecurityIpList|String|100.xxx.xxx.xxx/24,10.xxx.xxx.xxx|IP白名单分组下的IP列表，最多1000个。

 |
|RequestId|String|EFC9161F-15E3-4A6E-8A99-C09916D1F464|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=DescribeSecurityIps
&InstanceId=r-bp1xxxxxxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeSecurityIpsResponse>
  <SecurityIpGroups>
    <SecurityIpGroup>
      <SecurityIpList>127.0.0.1</SecurityIpList>
      <SecurityIpGroupAttribute/>
      <SecurityIpGroupName>default</SecurityIpGroupName>
    </SecurityIpGroup>
    <SecurityIpGroup>
      <SecurityIpList>100.xxx.xxx.xxx/24,10.xxx.xxx.xxx</SecurityIpList>
      <SecurityIpGroupAttribute>hidden</SecurityIpGroupAttribute>
      <SecurityIpGroupName>rds_replica_group</SecurityIpGroupName>
    </SecurityIpGroup>
  </SecurityIpGroups>
  <RequestId>EFC9161F-15E3-4A6E-8A99-C09916D1F464</RequestId>
</DescribeSecurityIpsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"SecurityIpGroups":{
		"SecurityIpGroup":[
			{
				"SecurityIpList":"127.0.0.1",
				"SecurityIpGroupAttribute":"",
				"SecurityIpGroupName":"default"
			},
			{
				"SecurityIpList":"100.xxx.xxx.xxx/24,10.xxx.xxx.xxx",
				"SecurityIpGroupAttribute":"hidden",
				"SecurityIpGroupName":"rds_replica_group"
			}
		]
	},
	"RequestId":"EFC9161F-15E3-4A6E-8A99-C09916D1F464"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

