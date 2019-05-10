# ModifyInstanceMajorVersion {#doc_api_R-kvstore_ModifyInstanceMajorVersion .reference}

调用ModifyInstanceMajorVersion升级Redis实例的大版本。

该API对应的控制台操作请参见[升级大版本](~~101764~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=ModifyInstanceMajorVersion)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|目标实例的ID。

 |
|MajorVersion|String|是|4.0|要升级到的大版本号，当前支持`4.0`。

 |
|Action|String|否|ModifyInstanceMajorVersion|系统规定参数，取值：ModifyInstanceMajorVersion。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |
|EffectTime|String|否|0|升级执行时间：

 -   0（立即执行）
-   1（在可维护时间段执行）

 **说明：** 默认为0。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|AA587FB2-2593-4DFE-BE13-2494C2DF0CBF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=ModifyInstanceMajorVersion
&InstanceId=r-bp1xxxxxxxxxxxxx
&MajorVersion=4.0
&EffectTime=0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyInstanceMajorVersionResponse>
  <RequestId>AA587FB2-2593-4DFE-BE13-2494C2DF0CBF</RequestId>
</ModifyInstanceMajorVersionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"AA587FB2-2593-4DFE-BE13-2494C2DF0CBF"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

