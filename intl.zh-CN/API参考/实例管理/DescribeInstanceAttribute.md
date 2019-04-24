# DescribeInstanceAttribute {#reference_nyk_w52_xdb .reference}

调用该API可以查询实例的详细信息。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共请求参数](intl.zh-CN/API参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|系统规定参数，取值：DescribeInstanceAttribute。|
|InstanceId|String|是|实例ID（全局唯一）|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|参见[公共返回参数](intl.zh-CN/API参考/公共参数.md#section_rjr_zgp_wbb)。|
|Instances|List|由DBInstanceAttribute组成的数组|

|参数|**类型**|**说明**|
|--|------|------|
|Config|String|实例的配置参数（JSON String），参见[实例配置参数表](intl.zh-CN/API参考/附表/实例配置参数表.md#)。|
|HasRenewChangeOrder|Boolean|是否有未生效的续费变配订单，取值：true或false。|
|InstanceId|String|实例ID （全局唯一）|
|ArchitectureType|String|指定架构类型返回实例列表：-   cluster（集群版）
-   standard（标准版）
-   SplitRW（读写分离版）
-   NULL（所有类型，默认值）

|
|ZoneId|String|RegionId下的可用区编码，参见[ZH-CN\_TP\_3191.md\#](intl.zh-CN/API参考/区域管理/DescribeRegions.md#)。|
|Engine|String|数据库类型|
|NetworkType|String|网络类型：-   CLASSIC（经典网络）
-   VPC（VPC网络）

|
|PackageType|String|请参见[资源包类型](https://help.aliyun.com/document_detail/90487.html?spm=5176.11065259.1996646101.searchclickresult.71254771hJtKfD%E3%80%82)。|
|QPS|String|每个时间间隔的每秒访问次数。|
|ReplicaId|String|数组的下标|
|IsRds|Boolean|是否为Rds参数，取值：true或false。|
|MaintainStartTime|String|可运维开始时间，返回格式HH:mmZ，如02:00Z。|
|VpcAuthMode|String|VPC认证模式，取值：Open。|
|EngineVersion|String|数据库版本：-   2.8
-   4.0

|
|Bandwidth|Long|实例带宽限制，单位：Mbps。|
|ChargeType|String|付费类型：-   PrePaid（预付费）
-   PostPaid（后付费）

|
|MaintainEndTime|String|可运维结束时间，返回格式：HH:mmZ，如02:00Z。|
|ReplicationMode|String|复制模式：-   master-slave（包括主从版和单节点版）
-   cluster（包括读写分离版与集群版）

|
|ConnectionDomain|String|Redis实例的连接域名（仅支持内网访问）。|
|InstanceType|String|实例类型，取值：Redis，Memcache。 默认为Redis。|
|InstanceStatus|String|实例状态|
|Port|Int|Redis连接端口|
|InstanceClass|String|实例规格|
|RegionId|String|申请的存储实例所在区域，参见[ZH-CN\_TP\_3191.md\#](intl.zh-CN/API参考/区域管理/DescribeRegions.md#)。|
|NodeType|String|节点类型|
|CreateTime|String|实例创建时间。采用ISO8601表示法，并使用UTC时间。格式为：YYYY-MM-DDThh:mm:ssZ。|
|AvailabilityValue|String|当月的可用性指标|
|EndTime|String|预付费实例到期时间。采用ISO8601表示法，并使用UTC时间。格式为：YYYY-MM-DDThh:mm:ssZ。|
|Capacity|Long|申请到的存储实例容量；单位：MB。|
|LuaStatus|String|脚本状态|
|Connections|Long|实例连接数限制，单位：个。|
|SecurityIPList|String|IP白名单|
|AuditLogRetention|String|SQL审计设置时长|

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com/
?Action=DescribeInstanceAttribute
&InstanceId=r-xxxxxxxxxxxxxxx
&<公共请求参数>
```

## 返回示例 {#section_hjp_tkw_wbb .section}

**XML格式**

```
<DescribeInstanceAttributeResponse>
 <RequestId>CA40C261-EB72-4EDA-AC57-958722162595</RequestId>
 <Instances>
   <DBInstanceAttribute>
     <Config>{"EvictionPolicy":"volatile-lru","list-max-ziplist-entries":512,"zset-max-ziplist-entries":128,"hash-max-ziplist-entries":512,"hash-max-ziplist-value":64,"list-max-ziplist-value":64,"set-max-intset-entries":512,"zset-max-ziplist-value":64}</Config>
     <HasRenewChangeOrder>false</HasRenewChangeOrder>
     <InstanceId>r-xxxxxxxxxxxxxxx</InstanceId>
     <ArchitectureType>standard</ArchitectureType>
     <ZoneId>cn-hangzhou-b</ZoneId>
     <Engine>Redis</Engine>
     <NetworkType>Classic</NetworkType>
     <PackageType>standard</PackageType>
     <QPS>100000</QPS>
     <ReplicaId>bls-xxxxxxxxxxxxxxx</ReplicaId>
     <IsRds>true</IsRds>
     <MaintainStartTime>18:00Z</MaintainStartTime>
     <VpcAuthMode>Open</VpcAuthMode>
     <ConnectionDomain>xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com</ConnectionDomain>
     <EngineVersion>4.0</EngineVersion>
     <Bandwidth>24</Bandwidth>
     <ChargeType>PrePaid</ChargeType>
     <MaintainEndTime>22:00Z</MaintainEndTime>
     <ReplicationMode>master-slave</ReplicationMode>
     <InstanceType>Redis</InstanceType>
     <InstanceStatus>Normal</InstanceStatus>
     <Port>6379</Port>
     <InstanceClass>redis.master.large.default</InstanceClass>
     <RegionId>cn-hangzhou</RegionId>
     <NodeType>double</NodeType>
     <CreateTime>2018-10-18T17:08:00Z</CreateTime>
     <AvailabilityValue>100.0%</AvailabilityValue>
     <EndTime>2019-01-18T16:00:00Z</EndTime>
     <Capacity>8192</Capacity>
     <LuaStatus>Enable</LuaStatus>
     <Connections>10000</Connections>
     <SecurityIPList>127.0.0.1</SecurityIPList>
   </DBInstanceAttribute>
 </Instances>
</DescribeInstanceAttributeResponse>
```

**JSON格式**

```
{
"RequestId":"CA40C261-EB72-4EDA-AC57-958722162595",
"Instances":{
 "DBInstanceAttribute":[{
   "Config":"{\"EvictionPolicy\":\"volatile-lru\",\"list-max-ziplist-entries\":512,\"zset-max-ziplist-entries\":128,\"hash-max-ziplist-entries\":512,\"hash-max-ziplist-value\":64,\"list-max-ziplist-value\":64,\"set-max-intset-entries\":512,\"zset-max-ziplist-value\":64}",
   "HasRenewChangeOrder":"false",
   "InstanceId":"r-xxxxxxxxxxxxxxx",
   "ArchitectureType":"standard",
   "ZoneId":"cn-hangzhou-b",
   "Engine":"Redis",
   "NetworkType":"Classic",
   "PackageType":"standard",
   "QPS":100000,
   "ReplicaId":"bls-xxxxxxxxxxxxxxx",
   "IsRds":true,
   "MaintainStartTime":"18:00Z",
   "VpcAuthMode":"Open",
   "ConnectionDomain":"xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com",
   "EngineVersion":"4.0",
   "Bandwidth":24,
   "ChargeType":"PrePaid",
   "MaintainEndTime":"22:00Z",
   "ReplicationMode":"master-slave",
   "InstanceType":"Redis",
   "InstanceStatus":"Normal",
   "Port":6379,
   "InstanceClass":"redis.master.large.default",
   "RegionId":"cn-hangzhou",
   "NodeType":"double",
   "CreateTime":"2018-10-18T17:08:00Z",
   "AvailabilityValue":"100.0%",
   "EndTime":"2019-01-18T16:00:00Z",
   "Capacity":8192,
   "LuaStatus":"Enable",
   "Connections":10000,
   "SecurityIPList":"127.0.0.1"
   					 }]
   		 }
}
```

