# ModifyInstanceSpec {#doc_api_R-kvstore_ModifyInstanceSpec .reference}

调用ModifyInstanceSpec变更Redis实例的规格。

各规格的详情请参见[实例规格表](~~107984~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=ModifyInstanceSpec)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyInstanceSpec|系统规定参数，取值：ModifyInstanceSpec。

 |
|InstanceClass|String|是|redis.master.small.default|变更后的实例规格，各规格的InstanceClass值请参见[实例规格表](~~107984~~)。

 |
|InstanceId|String|是|r-j6cxxxxxxxxxxxxx|目标实例的ID。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |
|AutoPay|Boolean|否|true|是否自动付款，可选值为：

 -   true（是）
-   false（否）

 **说明：** 不传默认为true。如果设置为false则需要在实例即将到期时在控制台[手动续费](~~26352~~)。

 |
|BusinessInfo|String|否|000000000|活动ID、业务信息。

 |
|CouponNo|String|否|youhuiquan\_promotion\_option\_id\_for\_blank|优惠码，默认值为：`youhuiquan_promotion_option_id_for_blank`。

 |
|EffectiveTime|String|否|Immediately|变更执行时间：

 -   Immediately（立即执行）
-   MaintainTime（运维时间执行）

 **说明：** 不传默认为Immediately。

 |
|ForceUpgrade|Boolean|否|true|是否强制变配：

 -   false（否）；
-   true（是）。

 **说明：** 默认为true。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|String|111111111111111|订单ID。

 |
|RequestId|String|0DA1D7EF-C80D-432C-8758-7D225182626B|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=ModifyInstanceSpec
&InstanceId=r-j6cxxxxxxxxxx3d4
&InstanceClass=redis.master.small.default
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyInstanceSpecResponse>
  <OrderId>111111111111111</OrderId>
  <RequestId>0DA1D7EF-C80D-432C-8758-7D225182626B</RequestId>
</ModifyInstanceSpecResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0DA1D7EF-C80D-432C-8758-7D225182626B",
	"OrderId":"111111111111111"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|PaymentMethodNotFound|No payment method has been registered on the account.|帐户上没有登记付款方法。|
|400|HasRenewChangeOrder|This instance has a renewChange order.|实例还有续费变配订单。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

