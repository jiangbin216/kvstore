# API概览 {#doc_3170 .concept}

云数据库Redis版提供以下OpenAPI。

## 生命周期管理 {#section_hnr_c7g_xxc .section}

|API|描述|
|---|--|
|[DescribeAvailableResource](cn.zh-CN/API参考/生命周期管理/DescribeAvailableResource.md)|查询指定可用区内可创建的实例。|
|[CreateInstance](cn.zh-CN/API参考/生命周期管理/CreateInstance.md)|创建一个Redis实例。|
|[ModifyInstanceSpec](cn.zh-CN/API参考/生命周期管理/ModifyInstanceSpec.md)|变更Redis实例的规格。|
|[TransformToPrePaid](cn.zh-CN/API参考/生命周期管理/TransformToPrePaid.md)|将按量付费的Redis实例转换为包年包月（预付费）实例。|
|[DeleteInstance](cn.zh-CN/API参考/生命周期管理/DeleteInstance.md)|释放Redis实例。|

## 区域管理 {#section_cmq_ksp_orp .section}

|API|描述|
|---|--|
|[MigrateToOtherZone](cn.zh-CN/API参考/区域管理/MigrateToOtherZone.md)|将Redis实例迁移到同地域内的其它可用区。|
|[DescribeRegions](cn.zh-CN/API参考/区域管理/DescribeRegions.md)|查询可创建Redis实例的地域。|
|[DescribeZones](cn.zh-CN/API参考/区域管理/DescribeZones.md)|查询支持Redis的可用区。|

## 连接管理 {#section_gsa_3la_pyu .section}

|API|描述|
|---|--|
|[AllocateInstancePublicConnection](cn.zh-CN/API参考/连接管理/AllocateInstancePublicConnection.md)|为Redis实例申请外网连接地址。|
|[ReleaseInstancePublicConnection](cn.zh-CN/API参考/连接管理/ReleaseInstancePublicConnection.md)|释放Redis实例的外网连接地址。|
|[ModifyIntranetAttribute](cn.zh-CN/API参考/连接管理/ModifyIntranetAttribute.md)|临时调整Redis实例的内网带宽。|
|[ModifyInstanceMinorVersion](cn.zh-CN/API参考/实例管理/ModifyInstanceMinorVersion.md#)|升级Redis实例的小版本。|
|[DescribeIntranetAttribute](cn.zh-CN/API参考/连接管理/DescribeIntranetAttribute.md)|查询Redis实例当前的内网带宽。如果使用了临时调整带宽功能，还可查询临时带宽的过期时间。|

## 实例管理 {#section_4qz_enk_4dq .section}

|API|描述|
|---|--|
|[DescribeDBInstanceNetInfo](cn.zh-CN/API参考/实例管理/DescribeDBInstanceNetInfo.md)|查看Redis实例的网络信息。|
|[DescribeInstanceAttribute](cn.zh-CN/API参考/实例管理/DescribeInstanceAttribute.md)|查询Redis实例的详细信息。|
|[DescribeInstances](cn.zh-CN/API参考/实例管理/DescribeInstances.md)|查询一个或多个Redis实例的信息。|
|[DescribeLogicInstanceTopology](cn.zh-CN/API参考/实例管理/DescribeLogicInstanceTopology.md)|查询Redis实例的逻辑拓扑结构。|
|[FlushInstance](cn.zh-CN/API参考/实例管理/FlushInstance.md)|清空Redis实例中的数据，不可恢复。|
|[ModifyInstanceAttribute](cn.zh-CN/API参考/实例管理/ModifyInstanceAttribute.md)|修改Redis实例的属性，包括名称和密码。|
|[ModifyInstanceMaintainTime](cn.zh-CN/API参考/实例管理/ModifyInstanceMaintainTime.md)|修改Redis实例的可维护时间段，阿里云将在您设定的可维护时间段内对Redis实例进行例行维护。|
|[ModifyInstanceNetExpireTime](cn.zh-CN/API参考/实例管理/ModifyInstanceNetExpireTime.md)|若Redis实例之前执行过由经典网络向VPC网络切换，并保留了经典网络连接地址，则可调用ModifyInstanceNetExpireTime延长经典网络连接地址的保存时间。|
|[ModifyDBInstanceConnectionString](cn.zh-CN/API参考/实例管理/ModifyDBInstanceConnectionString.md)|修改Redis实例的连接地址。|
|[SwitchNetwork](cn.zh-CN/API参考/实例管理/SwitchNetwork.md)|切换Redis实例的网络类型，支持从经典网络切换为VPC网络。|
|[ModifyInstanceMajorVersion](cn.zh-CN/API参考/实例管理/ModifyInstanceMajorVersion.md)|升级Redis实例的大版本。|
|[RestartInstance](cn.zh-CN/API参考/实例管理/RestartInstance.md)|重启运行中的Redis实例。|

## 续费管理 {#section_xez_dh8_euo .section}

|API|描述|
|---|--|
|[ModifyInstanceAutoRenewalAttribute](cn.zh-CN/API参考/续费管理/ModifyInstanceAutoRenewalAttribute.md)|开启或者关闭Redis实例的到期前自动续费功能。|
|[DescribePrice](cn.zh-CN/API参考/续费管理/DescribePrice.md)|查询创建Redis实例、升级配置或续费等操作产生的费用。|
|[DescribeInstanceAutoRenewalAttribute](cn.zh-CN/API参考/续费管理/DescribeInstanceAutoRenewalAttribute.md)|查看Redis实例的自动续费情况。|

## 账号管理 {#section_uce_qjt_4vl .section}

|API|描述|
|---|--|
|[DescribeAccounts](cn.zh-CN/API参考/账号管理/DescribeAccounts.md)|查找指定Redis实例的帐户列表信息或实例中某个账号的信息。|
|[ModifyAccountDescription](cn.zh-CN/API参考/账号管理/ModifyAccountDescription.md)|修改Redis账号的描述。|
|[ResetAccountPassword](cn.zh-CN/API参考/账号管理/ResetAccountPassword.md)|重置Redis账号的密码。|
|[CreateAccount](cn.zh-CN/API参考/账号管理/CreateAccount.md)|可以在Redis实例中创建有特定权限的账号。|
|[DeleteAccount](cn.zh-CN/API参考/账号管理/DeleteAccount.md)|删除一个Redis账号。|
|[GrantAccountPrivilege](cn.zh-CN/API参考/账号管理/GrantAccountPrivilege.md)|修改Redis账号的权限。|

## 备份恢复 {#section_jal_nec_mbw .section}

|API|描述|
|---|--|
|[CreateBackup](cn.zh-CN/API参考/备份恢复/CreateBackup.md)|为Redis实例创建数据备份。|
|[ModifyBackupPolicy](cn.zh-CN/API参考/备份恢复/ModifyBackupPolicy.md)|修改Redis实例的自动备份策略。|
|[DescribeBackupPolicy](cn.zh-CN/API参考/备份恢复/DescribeBackupPolicy.md)|查询Redis实例的备份策略，包括备份周期、备份时间等。|
|[DescribeBackups](cn.zh-CN/API参考/备份恢复/DescribeBackups.md)|查询Redis实例的备份文件信息。|
|[RestoreInstance](cn.zh-CN/API参考/备份恢复/RestoreInstance.md)|将备份文件中的数据恢复到指定的Redis实例中。|

## 监控管理 {#section_ghg_i80_mr2 .section}

|API|描述|
|---|--|
|[DescribeMonitorItems](cn.zh-CN/API参考/监控管理/DescribeMonitorItems.md)|查询Redis监控项列表。|
|[DescribeHistoryMonitorValues](cn.zh-CN/API参考/监控管理/DescribeHistoryMonitorValues.md)|查看Redis实例的历史监控信息。|

## 日志管理 {#section_bg4_wsb_bjf .section}

|API|描述|
|---|--|
|[DescribeAuditRecords](cn.zh-CN/API参考/日志管理/DescribeAuditRecords.md)|查看Redis实例的审计日志。|
|[DescribeRunningLogRecords](cn.zh-CN/API参考/日志管理/DescribeRunningLogRecords.md)|查询Redis实例的运行日志列表。|
|[DescribeSlowLogRecords](cn.zh-CN/API参考/日志管理/DescribeSlowLogRecords.md)|查询Redis实例在指定时间内产生的慢日志。|
|[ModifyAuditLogConfig](cn.zh-CN/API参考/日志管理/ModifyAuditLogConfig.md)|设置审计日志的保留天数。|

## 网络安全 {#section_xqf_fiv_67u .section}

|API|描述|
|---|--|
|[DescribeSecurityIps](cn.zh-CN/API参考/网络安全/DescribeSecurityIps.md)|查询允许访问Redis实例的IP名单。|
|[ModifySecurityIps](cn.zh-CN/API参考/网络安全/ModifySecurityIps.md)|设置Redis实例的IP白名单。|
|[ModifyInstanceSSL](cn.zh-CN/API参考/网络安全/ModifyInstanceSSL.md)|设置Redis实例的SSL加密模式。|
|[ModifyInstanceVpcAuthMode](cn.zh-CN/API参考/网络安全/ModifyInstanceVpcAuthMode.md)|开启或关闭免密访问。开启免密访问后，同一VPC内的云服务器不使用密码就可以访问Redis，同时仍然支持通过用户名及密码的方式连接Redis。|

## 参数管理 {#section_lwc_6ai_x6d .section}

|API|描述|
|---|--|
|[ModifyInstanceConfig](cn.zh-CN/API参考/参数管理/ModifyInstanceConfig.md)|修改Redis实例的配置参数。|
|[DescribeParameters](cn.zh-CN/API参考/参数管理/DescribeParameters.md)|查询Redis实例的配置参数和运行参数。|

## 性能优化 {#section_lq4_tj2_kgu .section}

|API|描述|
|---|--|
|[CreateCacheAnalysisTask](cn.zh-CN/API参考/性能优化/CreateCacheAnalysisTask.md)|手动发起缓存分析任务。|
|[DescribeCacheAnalysisReport](cn.zh-CN/API参考/性能优化/DescribeCacheAnalysisReport.md)|查看Redis实例在指定日期中的缓存分析报告。|
|[DescribeCacheAnalysisReportList](cn.zh-CN/API参考/性能优化/DescribeCacheAnalysisReportList.md)|查看Redis实例的缓存分析报告列表。|

