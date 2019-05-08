# CreateInstance {#reference_l2q_byx_wdb .reference}

调用该API可以创建一个实例。

创建实例所需的实例规格请参见[实例规格表](cn.zh-CN/API参考/附表/实例规格表.md#)。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共请求参数](cn.zh-CN/API参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|系统规定参数，取值：CreateInstance。|
|InstanceName|String|否|实例名称。 名称为2-128个字符，以大小写字英文母或中文开头，不支持字符@/:=”<\>\{\[\]\}和空格。|
|Password|String|否|实例密码。 字符类型，8-30个字符，需同时包含大写字母、小写字母和数字。 **说明：** 暂时不支持 !<\>\(\)\[\]\{\},\`~.-\_@\#$%^&\* 之类的特殊符号。

|
|InstanceClass|String|是|申请的Redis实例规格。参见[实例规格表](cn.zh-CN/API参考/附表/实例规格表.md#)。|
|RegionId|String|是|申请的存储实例所在区域。通过函数DescribeRegions查看可用的数据中心。|
|ZoneId|String|否|RegionId下的可用区。通过函数DescribeRegions查看可用的可用区。|
|ChargeType|String|否|付费类型：PrePaid或PostPaid，默认为PostPaid。|
|Period|Long|否|付费周期，付费类型为PrePaid时必须，单位为月，可选值：1-9，12，24，36。|
|Token|String|否|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，大小写敏感、不超过64个ASCII字符。|
|NetworkType|String|否| 网络类型：

 -   CLASSIC（经典网络）
-   VPC（专有网络）

 网络默认经典网络。

 |
|VpcId|String|否|VPC网络ID|
|VSwitchId|String|否|虚拟交换机ID|
|PrivateIp|String|否|私有IP地址|
|SrcDBInstanceId|String|否|基于某个实例的备份集创建实例有效，输入产生备份集的实例ID。|
|BackupId|String|否|基于某个实例的备份集创建实例有效，输入产生备份集ID。通过调用DescribeBackups查询BackupId。|
|InstanceType|String|否|实例类型，取值：Redis，Memcache。 默认为Redis。|
|EngineVersion|String|否|版本类型，取值：2.8或4.0。 默认值为2.8。|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|参数类型|描述|
|--|----|--|
|<公共返回参数\>|-|参见[公共返回参数](cn.zh-CN/API参考/公共参数.md#section_rjr_zgp_wbb)。|
|InstanceId|String|实例 ID （全局唯一）|
|InstanceName|String|实例名称|
|ChargeType|String|付费类型：PrePaid 或 PostPaid。默认为 PostPaid。|
|Config|String|实例的详细配置|
|ZoneId|String|RegionId 下的可用区编码。参见[ZH-CN\_TP\_3191.md\#](cn.zh-CN/API参考/区域管理/DescribeRegions.md#)。|
|InstanceStatus|String|实例的当前状态|
|Port|Int|Redis 连接端口|
|QPS|String|每个时间间隔的每秒访问次数|
|RegionId|String|申请的存储实例所在区域。参见[ZH-CN\_TP\_3191.md\#](cn.zh-CN/API参考/区域管理/DescribeRegions.md#)。|
|Capacity|Long|申请到的存储实例容量，单位：MB。|
|ConnectionDomain|String|Redis 实例的连接域名（仅支持内网访问）|
|Bandwidth|Long|实例带宽限制，单位：Mbps。|
|Connections|Long|实例连接数限制，单位：个。|

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com/
?Action=CreateInstances
&InstanceName=r-xxxxxxxxxxxxxxx
&RegionId=cn-hangzhou
&InstanceClass=redis.master.2xlarge.default
&<公共请求参数>
```

## 返回示例 {#section_hjp_tkw_wbb .section}

**XML格式**

```
<CreateInstances>
 <ChargeType>PostPaid</ChargeType>
 <Config>{"EvictionPolicy":"volatile-lru","list-max-ziplist-entries":512,"zset-max-ziplist-entries":128,"hash-max-ziplist-entries":512,"hash-max-ziplist-value":64,"list-max-ziplist-value":64,"set-max-intset-entries":512,"zset-max-ziplist-value":64}</Config>
 <InstanceId>r-xxxxxxxxxxxxxxx</InstanceId>
 <UserName>r-xxxxxxxxxxxxxxx</UserName>
 <ZoneId>cn-qingdao-b</ZoneId>
 <InstanceStatus>Creating</InstanceStatus>
 <Port>6379</Port>
 <QPS>100000</QPS>
 <RequestId>5DEA3CC9-F81D-4387-8E97-CEA40F09244D</RequestId>
 <RegionId>cn-qingdao</RegionId>
 <Capacity>32768</Capacity>
 <ConnectionDomain>r-xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com</ConnectionDomain>
 <Bandwidth>32</Bandwidth>
 <Connections>10000</Connections>
</CreateInstancesResponse>
```

**JSON格式**

```
{
   "ChargeType":"PostPaid",
   "Config":"{"EvictionPolicy":"volatile-lru","list-max-ziplist-entries":512,"zset-max-ziplist-entries":128,"hash-max-ziplist-entries":512,"hash-max-ziplist-value":64,"list-max-ziplist-value":64,"set-max-intset-entries":512,"zset-max-ziplist-value":64}",
   "InstanceId":"r-xxxxxxxxxxxxxxx",
   "UserName":"r-xxxxxxxxxxxxxxx",
   "ZoneId":"cn-qingdao-b",
   "InstanceStatus":"Creating",
   "Port":6379,
   "QPS":100000,
   "RequestId":"5DEA3CC9-F81D-4387-8E97-CEA40F09244D",
   "RegionId":"cn-qingdao",
   "Capacity":32768,
   "ConnectionDomain":"r-xxxxxxxxxxxxxxx.redis.rds.aliyuncs.com",
   "Bandwidth":32,
   "Connections":10000
}
```

