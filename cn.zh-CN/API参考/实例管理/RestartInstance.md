# RestartInstance {#doc_api_R-kvstore_RestartInstance .reference}

调用RestartInstance重启运行中的实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=RestartInstance)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RestartInstance|系统规定参数，取值：RestartInstance。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|目标实例的ID。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |
|EffectiveTime|String|否|1|重启时间：

 -   0（立即重启）
-   1（运维时间重启）

 **说明：** 默认为0。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|InstanceId|String|r-bp1xxxxxxxxxxxxx|实例ID。

 |
|TaskId|String|111111111|任务ID。

 |
|RequestId|String|EFC9161F-15E3-4A6E-8A99-C33331F464|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=RestartInstance
&InstanceId=r-bp1xxxxxxxxxxxxx
&EffectiveTime=1
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RestartInstanceResponse>
  <RequestId>EFC9161F-15E3-4A6E-8A99-C33331F464</RequestId>
  <InstanceId>r-bp1xxxxxxxxxxxxx</InstanceId>
  <TaskId>111111111</TaskId>
</RestartInstanceResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"InstanceId":"r-bp1xxxxxxxxxxxxx",
	"RequestId":"EFC9161F-15E3-4A6E-8A99-6661F464",
	"TaskId":"111111111"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

