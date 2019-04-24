# DescribeAccounts {#doc_api_R-kvstore_DescribeAccounts .reference}

调用DescribeAccounts查找指定实例的帐户列表信息或实例中某个账号的信息。

**说明：** 该API仅支持4.0版本的Redis实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=DescribeAccounts)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAccounts|系统规定参数，取值：DescribeAccounts。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|账号所属实例的ID。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |
|AccountName|String|否|demoaccount|账号名。以小写字母开头，由小写字母、数字或下划线组成，长度不超过16个字符。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Accounts| | |由账号信息组成的集合。

 |
|└AccountDescription|String|this is a test account|账号备注信息。

 |
|└AccountName|String|demoaccount|账号名称。

 |
|└AccountStatus|String|Available|账号状态：

 -   Unavailable（不可用）
-   Available（可用）

 |
|└AccountType|String|Normal|账号类型：

 -   Normal（普通账号）
-   Super（超级账号）

 |
|└DatabasePrivileges| | |账号权限列表。

 |
|└AccountPrivilege|String|RoleReadWrite|账号权限：

 -   RoleReadOnly（只读）
-   RoleReadWrite（读写）

 |
|└InstanceId|String|r-bp1xxxxxxxxxxxxx|实例ID。

 |
|RequestId|String|6C9E114C-217C-4118-83C0-B40702221161|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeAccounts
&InstanceId=r-bp1xxxxxxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeAccountsResponse>
  <Accounts>
    <Account>
      <DatabasePrivileges>
        <DatabasePrivilege>
          <AccountPrivilege>RoleReadWrite</AccountPrivilege>
        </DatabasePrivilege>
      </DatabasePrivileges>
      <AccountStatus>Available</AccountStatus>
      <InstanceId>r-bp1xxxxxxxxxxxxx</InstanceId>
      <AccountName>r-bp1xxxxxxxxxxxxx</AccountName>
      <PrivExceeded>0</PrivExceeded>
      <AccountType>Normal</AccountType>
    </Account>
  </Accounts>
  <RequestId>6C9E114C-217C-4118-83C0-B40702221161</RequestId>
</DescribeAccountsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Accounts":{
		"Account":[
			{
				"AccountStatus":"Available",
				"DatabasePrivileges":{
					"DatabasePrivilege":[
						{
							"AccountPrivilege":"RoleReadWrite"
						}
					]
				},
				"InstanceId":"r-bp1xxxxxxxxxxxxx",
				"AccountName":"r-bp1xxxxxxxxxxxxx",
				"PrivExceeded":"0",
				"AccountType":"Normal"
			}
		]
	},
	"RequestId":"6C9E114C-217C-4118-83C0-B40702221161"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

