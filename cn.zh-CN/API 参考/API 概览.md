# API 概览 {#concept_t53_hsn_tdb .concept}

本文汇总了云数据库RDS所有可调用的API，各API的具体信息请参见相关文档。

## 实例生命周期管理接口 { .section}

|API|描述|
|---|--|
|CreateInstance|创建实例|
|DeleteInstance|释放实例|
|ModifyInstanceSpec|变更实例|
|TransformToPrePaid|付费类型转换|

## 实例管理接口 { .section}

|API|描述|
|---|--|
|ModifyInstanceAttribute|修改实例属性|
|FlushInstance|清空实例|
|DescribeInstances|查询实例基础信息|
|DescribeInstanceAttribute|查询实例详情|
|DescribeSecurityIps|查询允许访问实例的 IP 名单|
|ModifyInstanceMaintainTime|修改实例可运维时间|
|ModifySecurityIps|修改实例白名单|
|DescribeRegions|查询实例可售卖地域|
|SwitchNetwork|修改网络类型|
|ModifyInstanceNetExpireTime|修改经典网络域名的保留时间|

## 备份恢复接口 { .section}

|API|描述|
|---|--|
|CreateBackup|创建备份|
|ModifyBackupPolicy|修改备份策略|
|DescribeBackupPolicy|查询备份策略|
|DescribeBackups|显示备份列表|
|RestoreInstance|基于备份集回滚实例|

## 监控管理接口 { .section}

|API|描述|
|---|--|
|DescribeMonitorItems|查看监控项列表|
|DescribeHistoryMonitorValues|查看历史监控|

## 参数管理接口 { .section}

|API|描述|
|---|--|
|DescribeParameters|查看实例参数配置|
|ModifyInstanceConfig|修改参数配置|

