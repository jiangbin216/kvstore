# DescribeDBInstanceNetInfo {#reference_ih5_zt2_xdb .reference}

调用该API可以查看实例的经典网络访问地址。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|-|参见[公共请求参数](intl.zh-CN/API参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|系统规定参数，取值：DescribeDBInstanceNetInfo。|
|InstanceId|String|是|实例ID（全局唯一）|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|参见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_rjr_zgp_wbb)。|
|NetInfoItems|List|由InstanceNetInfo组成的实例连接信息|
|InstanceNetworkType|String|实例的网络类型：-   VPC（专有网络）
-   Classic（经典网络）

|

|名称|类型|描述|
|--|--|--|
|ConnectionString|String|连接地址|
|IPAddress|String|IP地址|
|IPType|String|IP网络类型：-   Private（私网，VPC内网）
-   Inner（保留的经典网络IP）

|
|Port|String|端口信息|
|VPCId|String|VPC ID|
|Upgradeable|String|过期时间，即剩余有效时间，以秒为单位。`0`表示不会过期。|

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com/
?Action=DescribeDBInstanceNetInfo
&InstanceId=r-xxxxxxxxxxxxxxx
&<公共请求参数>
```

## 返回示例 {#section_jzf_dbg_qfb .section}

**XML格式**

```
<DescribeDBInstanceNetInfoResponse>
 <RequestId>314C4FB3-4256-424F-9AD9-1A6B3444160A</RequestId>
 <InstanceNetworkType>Classic</InstanceNetworkType>
 <NetInfoItems>
   <InstanceNetInfo>
     <DBInstanceNetType>1</DBInstanceNetType>
     <Port>6379</Port>
     <ConnectionString>r-xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com</ConnectionString>
     <VPCId></VPCId>
     <IPAddress>xxx.xxx.xxx.xxx</IPAddress>
     <IPType>Inner</IPType>
     <Upgradeable>0</Upgradeable>
   </InstanceNetInfo>
 </NetInfoItems>
</DescribeDBInstanceNetInfoResponse>
```

**JSON格式**

```
{
 "RequestId":"314C4FB3-4256-424F-9AD9-1A6B3444160A",
 "InstanceNetworkType":"Classic",
 "NetInfoItems":{
   "InstanceNetInfo":[{
     "DBInstanceNetType":"1",
     "Port":"6379",
     "ConnectionString":"r-xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com",
     "VPCId":"",
     "IPAddress":"xxx.xxx.xxx.xxx",
     "IPType":"Inner",
     "Upgradeable":"0"
   				   }]
   			 }
}
```

