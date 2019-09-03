# DescribeInstanceSSL {#doc_api_R-kvstore_DescribeInstanceSSL .reference}

调用DescribeInstanceSSL查看Redis实例是否开启了SSL加密认证。

Redis 2.8标准版、集群版实例和Redis 4.0集群版实例支持SSL加密。您可以启用SSL（Secure Socket Layer）加密，提高数据传输的安全性。

您可以在以下方法中任选其一来开启或关闭Redis实例的SSL加密功能，或者更新证书的有效期：

-   调用[ModifyInstanceSSL](~~96194~~)。
-   在Redis控制台设置，操作步骤请参见[设置SSL加密](~~84898~~)。

**说明：** 开启SSL加密会增加实例的网络响应时间。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=R-kvstore&api=DescribeInstanceSSL&type=RPC&version=2015-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|实例ID。

 |
|Action|String|否|DescribeInstanceSSL|系统规定参数，取值：DescribeInstanceSSL。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|SSLEnabled|String|Enable|SSL加密功能的状态：

 -   Enable（已开启）
-   Disable（未开启）

 |
|SSLExpiredTime|String|2020-08-05T09:05:53Z|SSL证书的过期时间。

 |
|InstanceId|String|r-bp1xxxxxxxxxxxxx|实例ID。

 |
|RequestId|String|02260F96-913E-4655-9BA5-A3651CAF3045|请求ID。

 |
|CertCommonName|String|r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com|SSL证书的common name，一般为需要申请SSL证书的域名，默认值为实例的内网连接地址。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=DescribeInstanceSSL
&InstanceId=r-bp1xxxxxxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeInstanceSSLResponse>
	  <SSLEnabled>Enable</SSLEnabled>
	  <SSLExpiredTime>2020-08-05T09:05:53Z</SSLExpiredTime>
	  <InstanceId>r-r-bp1xxxxxxxxxxxxx</InstanceId>
	  <RequestId>02260F96-913E-4655-9BA5-A3651CAF3045</RequestId>
	  <CertCommonName>r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com</CertCommonName>
</DescribeInstanceSSLResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"SSLEnabled":"Enable",
	"SSLExpiredTime":"2020-08-05T09:05:53Z",
	"RequestId":"02260F96-913E-4655-9BA5-A3651CAF3045",
	"InstanceId":"r-bp1xxxxxxxxxxxxx",
	"CertCommonName":"r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/R-kvstore)查看更多错误码。

