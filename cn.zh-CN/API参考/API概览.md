# API概览 {#doc_api_overview .concept}

云数据库Redis版提供以下相关API接口。

**说明：** SDK代码示例与更多API资源请访问[API Explorer](https://api.aliyun.com/)。

## 生命周期管理 { .section}

|API|描述|
|---|--|
|[CreateInstance](cn.zh-CN/API参考/生命周期管理/CreateInstance.md#)|创建一个Redis实例。|
|[DeleteInstance](cn.zh-CN/API参考/生命周期管理/DeleteInstance.md#)|释放Redis实例。|
|[ModifyInstanceSpec](cn.zh-CN/API参考/生命周期管理/ModifyInstanceSpec.md#)|变更Redis实例的规格。|
|[TransformToPrePaid](cn.zh-CN/API参考/生命周期管理/TransformToPrePaid.md#)|将按量付费的Redis实例转换为包年包月（预付费）实例。|

## 区域管理 {#section_iwt_qhr_bmt .section}

|API|描述|
|---|--|
|[DescribeRegions](cn.zh-CN/API参考/区域管理/DescribeRegions.md#)|查询可创建Redis实例的地域。|
|[DescribeZones](cn.zh-CN/API参考/区域管理/DescribeZones.md#)|查询支持Redis的可用区。|
|[MigrateToOtherZone](cn.zh-CN/API参考/区域管理/MigrateToOtherZone.md#)|将Redis实例迁移到同地域内的其它可用区。|

## 实例管理 {#section_jhk_02h_r6k .section}

|API|描述|
|---|--|
|[DescribeDBInstanceNetInfo](cn.zh-CN/API参考/实例管理/DescribeDBInstanceNetInfo.md#)|查看Redis实例的网络信息。|
|[DescribeInstanceAttribute](cn.zh-CN/API参考/实例管理/DescribeInstanceAttribute.md#)|查询Redis实例的详细信息。|
|[DescribeInstances](cn.zh-CN/API参考/实例管理/DescribeInstances.md#)|查询一个或多个Redis实例的信息。|
|[DescribeLogicInstanceTopology](cn.zh-CN/API参考/实例管理/DescribeLogicInstanceTopology.md#)|查询Redis实例的逻辑拓扑结构。|
|[FlushInstance](cn.zh-CN/API参考/实例管理/FlushInstance.md#)|清空Redis实例中的数据。|
|[ModifyInstanceAttribute](cn.zh-CN/API参考/实例管理/ModifyInstanceAttribute.md#)|修改Redis实例的属性，包括名称和密码。|
|[ModifyInstanceMaintainTime](cn.zh-CN/API参考/实例管理/ModifyInstanceMaintainTime.md#)|修改Redis实例的可维护时间段。|
|[ModifyInstanceNetExpireTime](cn.zh-CN/API参考/实例管理/ModifyInstanceNetExpireTime.md#)|延长经典网络连接地址的保存时间。|
|[ModifyDBInstanceConnectionString](cn.zh-CN/API参考/实例管理/ModifyDBInstanceConnectionString.md#)|修改Redis实例的连接地址。|
|[SwitchNetwork](cn.zh-CN/API参考/实例管理/SwitchNetwork.md#)|切换Redis实例的网络类型，支持从经典网络切换为VPC网络。|
|[ModifyInstanceMajorVersion](cn.zh-CN/API参考/实例管理/ModifyInstanceMajorVersion.md#)|升级Redis实例的大版本。|
|[RestartInstance](cn.zh-CN/API参考/实例管理/RestartInstance.md#)|重启运行中的Redis实例。|

## 续费管理 {#section_x6s_0q9_7bv .section}

|API|描述|
|---|--|
|[ModifyInstanceAutoRenewalAttribute](cn.zh-CN/API参考/续费管理/ModifyInstanceAutoRenewalAttribute.md#)|开启或者关闭Redis实例的到期前自动续费功能。|
|[DescribePrice](cn.zh-CN/API参考/续费管理/DescribePrice.md#)|查询创建Redis实例、升级配置或续费等操作产生的费用。|
|[DescribeInstanceAutoRenewalAttribute](cn.zh-CN/API参考/续费管理/DescribeInstanceAutoRenewalAttribute.md#)|查看Redis实例的自动续费情况。|

## 备份恢复 {#section_ejj_0mf_0us .section}

|API|描述|
|---|--|
|[CreateBackup](cn.zh-CN/API参考/备份恢复/CreateBackup.md#)|为Redis实例创建数据备份。|
|[ModifyBackupPolicy](cn.zh-CN/API参考/备份恢复/ModifyBackupPolicy.md#)|修改Redis实例的自动备份策略。|
|[DescribeBackupPolicy](cn.zh-CN/API参考/备份恢复/DescribeBackupPolicy.md#)|查询Redis实例的备份策略，包括备份周期、备份时间等。|
|[DescribeBackups](cn.zh-CN/API参考/备份恢复/DescribeBackups.md#)|查询Redis实例的备份文件信息。|
|[RestoreInstance](cn.zh-CN/API参考/备份恢复/RestoreInstance.md#)|将备份文件中的数据恢复到指定的Redis实例中。|

## 监控管理 {#section_bhg_c95_0yz .section}

|API|描述|
|---|--|
|[DescribeMonitorItems](cn.zh-CN/API参考/监控管理/DescribeMonitorItems.md#)|查询Redis监控项列表。|
|[DescribeHistoryMonitorValues](cn.zh-CN/API参考/监控管理/DescribeHistoryMonitorValues.md#)|查看Redis实例的历史监控信息。|

## 日志管理 { .section}

|API|描述|
|---|--|
|[DescribeAuditRecords](cn.zh-CN/API参考/日志管理/DescribeAuditRecords.md#)|查看Redis实例的审计日志。|
|[DescribeRunningLogRecords](cn.zh-CN/API参考/日志管理/DescribeRunningLogRecords.md#)|查询Redis实例的运行日志列表。|
|[DescribeSlowLogRecords](cn.zh-CN/API参考/日志管理/DescribeSlowLogRecords.md#)|查询Redis实例在指定时间内产生的慢日志。|

## 账号管理 {#section_c8z_fci_n7w .section}

|API|描述|
|---|--|
|[DescribeAccounts](cn.zh-CN/API参考/账号管理/DescribeAccounts.md#)|查找指定Redis实例的帐户列表信息或实例中某个账号的信息。|
|[ModifyAccountDescription](cn.zh-CN/API参考/账号管理/ModifyAccountDescription.md#)|修改Redis账号的描述。|
|[ResetAccountPassword](cn.zh-CN/API参考/账号管理/ResetAccountPassword.md#)|重置Redis账号的密码。|
|[CreateAccount](cn.zh-CN/API参考/账号管理/CreateAccount.md#)|在Redis实例中创建有特定权限的账号。|
|[DeleteAccount](cn.zh-CN/API参考/账号管理/DeleteAccount.md#)|删除一个Redis账号。|
|[GrantAccountPrivilege](cn.zh-CN/API参考/账号管理/GrantAccountPrivilege.md#)|修改Redis账号的权限。|

## 网络安全 {#section_2bz_zhh_hul .section}

|API|描述|
|---|--|
|[ModifyInstanceSSL](cn.zh-CN/API参考/网络安全/ModifyInstanceSSL.md#)|设置Redis实例的SSL加密模式。|
|[ModifySecurityIps](cn.zh-CN/API参考/网络安全/ModifySecurityIps.md#)|设置Redis实例的IP白名单。|
|[ModifyInstanceVpcAuthMode](cn.zh-CN/API参考/网络安全/ModifyInstanceVpcAuthMode.md#)|开启或关闭免密访问。|
|[DescribeSecurityIps](cn.zh-CN/API参考/网络安全/DescribeSecurityIps.md#)|查询允许访问Redis实例的IP名单。|

## 参数管理 {#section_9mh_9zq_8ma .section}

|API|描述|
|---|--|
|[DescribeParameters](cn.zh-CN/API参考/参数管理/DescribeParameters.md#)|查询Redis实例的配置参数和运行参数。|
|[ModifyInstanceConfig](cn.zh-CN/API参考/参数管理/ModifyInstanceConfig.md#)|修改Redis实例的配置参数。|

