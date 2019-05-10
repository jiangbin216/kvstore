# RestoreInstance {#doc_api_R-kvstore_RestoreInstance .reference}

调用RestoreInstance将备份文件中的数据恢复到指定的Redis实例中。

该API对应的控制台操作请参见[备份与恢复](~~43886~~)。

**说明：** 调用此API会使用备份数据覆盖Redis实例的现有数据，风险较大，请务必谨慎操作。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=RestoreInstance)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RestoreInstance|系统规定参数，取值：RestoreInstance。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|需要进行数据恢复的实例的ID。

 |
|BackupId|String|是|111111111|备份文件ID。您可以调用[DescribeBackups](~~61081~~)查询。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8D0C0AFC-E9CD-47A4-8395-5C31BF9B3E76|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com
?Action=RestoreInstance
&InstanceId=r-bp1xxxxxxxxxxxxx
&BackupId=111111111
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RestoreInstanceResponse>
  <RequestId>8D0C0AFC-E9CD-47A4-8395-5C31BF9B3E76</RequestId>
</RestoreInstanceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8D0C0AFC-E9CD-47A4-8395-5C31BF9B3E76"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

