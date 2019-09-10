# ModifyInstanceMaintainTime {#doc_api_R-kvstore_ModifyInstanceMaintainTime .reference}

调用ModifyInstanceMaintainTime修改Redis实例的可维护时间段，阿里云将在您设定的可维护时间段内对Redis实例进行例行维护。

该API对应的控制台操作请参见[设置可维护时间段](~~55252~~)。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=R-kvstore&api=ModifyInstanceMaintainTime&type=RPC&version=2015-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|目标实例的ID。

 |
|MaintainStartTime|String|是|03:00Z|可维护时间段的开始时间，格式：`HH:mmZ`。

 |
|MaintainEndTime|String|是|02:00Z|可维护时间段的结束时间，格式：`HH:mmZ`。

 **说明：** 开始时间和结束时间的间隔应为1小时，如：MaintainStartTime为`01:00Z`，MaintainEndTime为`02:00Z`。

 |
|Action|String|否|ModifyInstanceMaintainTime|系统规定参数，取值：ModifyInstanceMaintainTime。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8D0C0AFC-E9CD-47A4-8395-5C31BF9B3E76|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=ModifyInstanceMaintainTime
&InstanceId=r-bp1xxxxxxxxxxxxx
&MaintainStartTime=02:00Z
&MaintainEndTime=03:00Z
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyInstanceMaintainTimeResponse>
      <RequestId>8D0C0AFC-E9CD-47A4-8395-5C31BF9B3E76</RequestId>
</ModifyInstanceMaintainTimeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8D0C0AFC-E9CD-47A4-8395-5C31BF9B3E76"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidEndTime.Format|Specified end time is not valid.|时间验证失败|

访问[错误中心](https://error-center.aliyun.com/status/product/R-kvstore)查看更多错误码。

