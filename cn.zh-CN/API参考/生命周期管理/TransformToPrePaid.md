# TransformToPrePaid {#doc_api_R-kvstore_TransformToPrePaid .reference}

调用TransformToPrePaid转换实例付费类型，将按量付费实例转换为包年包月（预付费）实例。

**说明：** 包年包月实例暂不支持转换到按量付费实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=TransformToPrePaid)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|TransformToPrePaid|系统规定参数，取值：TransformToPrePaid。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|需要转换付费类型的实例的ID。

 |
|Period|Long|是|12|预付费时长，单位是月。取值范围为：1-9、12、24、36。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |
|AutoPay|Boolean|否|true|是否自动付款。可选值：

 -   true
-   false

 **说明：** 不传默认为true。如果设置为false则需要在实例即将到期时在控制台手动[续费](~~26352~~)。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|EndTime|String|2019-01-18T16:00:00Z|实例付费方式转换为包年包月后的实例到期时间。

 |
|OrderId|String|111111111111111|订单ID。

 |
|RequestId|String|426F1356-B6EF-4DAD-A1C3-DE53B9DAF586|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=TransformToPrePaid
&InstanceId=r-bp1xxxxxxxxxxxxx
&Period=12
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<TransformToPrePaidResponse>
  <OrderId>111111111111111</OrderId>
  <RequestId>426F1356-B6EF-4DAD-A1C3-DE53B9DAF586</RequestId>
  <EndTime>2019-01-18T16:00:00Z</EndTime>
</TransformToPrePaidResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"426F1356-B6EF-4DAD-A1C3-DE53B9DAF586",
	"OrderId":"111111111111111",
	"EndTime":"2019-01-18T16:00:00Z"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|MissingParameter|Period is mandatory for this action.|实例Id是必传参数|
|400|InvalidParam|Period is invalid|购买时长非法。|
|403|AlreadyPrePaid|This instance is already prepaid|该实例已经成为预付费实例。|
|400|ResourceNotAvailable|Resource you requested is not available for finance user.|您所请求的资源对财务用户来说是不可用的。|
|400|InsufficientBalance|Your account does not have enough balance.|账户余额不足，请先充值再操作。|
|403|RealNameAuthenticationError|Your account has not passed the real-name authentication yet.|您的帐户还没有通过实名认证。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

