# DescribeLogicInstanceTopology {#doc_api_R-kvstore_DescribeLogicInstanceTopology .reference}

调用DescribeLogicInstanceTopology返回指定实例的逻辑拓扑结构。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=R-kvstore&api=DescribeLogicInstanceTopology)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLogicInstanceTopology|系统规定参数，取值：DescribeLogicInstanceTopology。

 |
|InstanceId|String|是|r-bp1xxxxxxxxxxxxx|目的实例的ID。

 |
|AccessKeyId|String|否|Lxxxxxxxxxxxxxxw|阿里云颁发给用户的访问服务所用的密钥ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|InstanceId|String|r-bp1xxxxxxxxxxxxx|实例的ID。

 |
|RedisProxyList| | |代理详情，包含代理节点信息。

 |
|└Bandwidth|String|96|节点的带宽限制，单位为MB/s。

 |
|└Capacity|String|5120|节点的容量，单位为MB。

 |
|└Connection|String|320000|连接数限制。

 |
|└NodeId|String|r-xxxxxxxxxxxxxxx-proxy-3\#5425423|节点ID。

 |
|└NodeType|String|proxy|节点类型，取值：

 -   proxy（代理节点）
-   db（数据节点）

 |
|RedisShardList| | |分片详情，包含NodeInfo等子节点信息 。

 |
|└Bandwidth|String|96|节点的带宽限制，单位为MB/s。

 |
|└Capacity|String|2048|节点的容量，单位为MB。

 |
|└Connection|String|10000|连接数限制。

 |
|└NodeId|String|r-bp1xxxxxxxxxxxxx-db-0\#6889415|节点ID。

 |
|└NodeType|String|db|节点类型，取值：

 -   proxy（代理节点）
-   db（数据节点）

 |
|RequestId|String|5F749626-2B6A-4DC2-A010-B51F7C33084E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://r-kvstore.aliyuncs.com/
?Action=DescribeLogicInstanceTopology
&InstanceId=r-bp1xxxxxxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLogicInstanceTopologyResponse>
  <RedisShardList>
    <NodeInfo>
      <NodeId>r-xxxxxxxxxxxxxxx-proxy-3#5425423</NodeId>
      <NodeType>proxy</NodeType>
      <Capacity>5120</Capacity>
      <Connection>320000</Connection>
      <Bandwidth>96</Bandwidth>
    </NodeInfo>
  </RedisShardList>
  <InstanceId>r-xxxxxxxxxxxxxxx</InstanceId>
  <RequestId>5F749626-2B6A-4DC2-A010-B51F7C33084E</RequestId>
</DescribeLogicInstanceTopologyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RedisShardList":{
		"NodeInfo":[
			{
				"NodeId":"r-xxxxxxxxxxxxxxx-proxy-3#5425423",
				"NodeType":"proxy",
				"Capacity":"5120",
				"Connection":"320000",
				"Bandwidth":96
			}
		]
	},
	"RequestId":"5F749626-2B6A-4DC2-A010-B51F7C33084E",
	"InstanceId":"r-xxxxxxxxxxxxxxx"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/R-kvstore)

