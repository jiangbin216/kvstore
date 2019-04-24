# ModifyInstanceAutoRenewalAttribute {#doc_api_R-kvstore_ModifyInstanceAutoRenewalAttribute .reference}

调用ModifyInstanceAutoRenewalAttribute开启或者关闭实例到期前自动续费的功能。

**说明：** 自动续费将于实例到期前7天触发。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=ModifyInstanceAutoRenewalAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyInstanceAutoRenewalAttribute|系统规定参数，取值：ModifyInstanceAutoRenewalAttribute。

 |
|DBInstanceId|String|是|r-bp1xxxxxxxxxxxxx|目标实例的ID。多个实例ID用半角逗号（‘,’）拼接，最多允许传入30个实例ID。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |
|Duration|String|否|3|自动续费周期，当AutoRenew=True时，该值有效且必传，取值范围为1-12。实例到期时，将以月为单位进行自动续费，月数等于该值。

 |
|AutoRenew|String|否|True|开启或关闭自动续费，取值可为：

 -   True（开启）
-   False（关闭）

 **说明：** 不传默认为False，即关闭自动续费。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|52D901ED-E0A5-42FB-B9DB-39C295C37738|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=ModifyInstanceAutoRenewalAttribute
&DBInstanceId=r-bp1xxxxxxxxxxxxx
&AutoRenew=True
&Duration=1
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyInstanceAutoRenewalAttributeResponse>
  <RequestId>52D901ED-E0A5-42FB-B9DB-39C295C37738</RequestId>
</ModifyInstanceAutoRenewalAttributeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"52D901ED-E0A5-42FB-B9DB-39C295C37738"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

