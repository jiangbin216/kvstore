# ReleaseInstancePublicConnection {#doc_api_R-kvstore_ReleaseInstancePublicConnection .reference}

调用ReleaseInstancePublicConnection释放Redis实例的外网连接地址。

该API对应的控制台操作请参见[释放外网连接地址](~~125424~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=ReleaseInstancePublicConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|实例ID。

 |
|CurrentConnectionString|String|是|r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com|外网连接地址。

 |
|Action|String|否|ReleaseInstancePublicConnection|系统规定参数，取值：ReleaseInstancePublicConnection。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|88F850B5-CC68-48B4-83CA-5497C3C191DE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=ReleaseInstancePublicConnection
&InstanceId=r-bp1xxxxxxxxxxxxx
&CurrentConnectionString=r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ReleaseInstancePublicConnectionResponse>
  <RequestId>88F850B5-CC68-48B4-83CA-5497C3C191DE</RequestId>
</ReleaseInstancePublicConnectionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"88F850B5-CC68-48B4-83CA-5497C3C191DE"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/R-kvstore)查看更多错误码。

