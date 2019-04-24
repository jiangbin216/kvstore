# MigrateToOtherZone {#doc_api_R-kvstore_MigrateToOtherZone .reference}

调用MigrateToOtherZone将实例迁移至同地域内的其它可用区。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=MigrateToOtherZone)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|MigrateToOtherZone|系统规定参数，取值：MigrateToOtherZone。

 |
|DBInstanceId|String|是|r-bp1xxxxxxxxxxxxx|实例 ID（全局唯一）。

 |
|ZoneId|String|是|cn-hangzhou-g|要迁移到的可用区（即目的可用区），您可以调用[DescribeZones](~~94527~~)接口查询可用区。

 |
|VSwitchId|String|否|vsw-sdrxxxxxxxxxxxxxxxxxx|虚拟交换机的ID 。

 **说明：** 

-   VSwitch所在可用区须与ZoneId（目的可用区）一致；
-   如果实例的网络类型为VPC，则该参数为必选。

 |
|EffectiveTime|String|否|Immediately|数据迁移后执行数据库切换的时间。可选值：

 -   Immediately（迁移完立即切换）
-   MaintainTime（可维护时间段内切换）

 **说明：** 默认为Immediately，迁移完立即切换。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|29B0BF34-D069-4495-92C7-FA6D94528A9E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=MigrateToOtherZone
&DBInstanceId=r-bp1xxxxxxxxxxxxx
&ZoneId=cn-hangzhou-g
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<MigrateToOtherZoneResponse>
  <RequestId>29B0BF34-D069-4495-92C7-FA6D94528A9E</RequestId>
</MigrateToOtherZoneResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"29B0BF34-D069-4495-92C7-FA6D94528A9E"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

