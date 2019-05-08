# ModifyInstanceVpcAuthMode {#doc_api_R-kvstore_ModifyInstanceVpcAuthMode .reference}

调用ModifyInstanceVpcAuthMode开启或关闭免密访问。开启免密访问后，同一VPC内的云服务器不使用密码就可以访问Redis，同时仍然支持通过用户名及密码的方式连接Redis。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=ModifyInstanceVpcAuthMode)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyInstanceVpcAuthMode|系统规定参数，取值：ModifyInstanceVpcAuthMode。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|需要修改设置的实例的ID。

 |
|VpcAuthMode|String|是|Close|VPC认证模式：

 -   Open（需要密码认证）
-   Close（关闭密码认证，即VPC免密）

 **说明：** 默认为Open。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|ABAF95F6-35C1-4177-AF3A-70969EBDF623|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=ModifyInstanceVpcAuthMode
&InstanceId=r-bp1xxxxxxxxxxxxx
&VpcAuthMode=Close
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyInstanceVpcAuthModeResponse>
  <RequestId>ABAF95F6-35C1-4177-AF3A-70969EBDF623</RequestId>
</ModifyInstanceVpcAuthModeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"ABAF95F6-35C1-4177-AF3A-70969EBDF623"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

