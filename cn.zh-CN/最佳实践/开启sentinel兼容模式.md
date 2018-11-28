# 开启sentinel兼容模式 {#task_vcv_hlx_wfb .task}

目前很多自建Redis使用sentinel做高可用，因此也使用了支持sentinel的客户端，为了方便用户上云，阿里云Redis开发了sentinel兼容模式以适应各种业务场景。

1.  登录[Redis 管理控制台](https://kvstore.console.aliyun.com/)。 
2.  单击实例ID，进入实例信息页面。 
3.  单击左侧导航栏的参数设置，进入参数设置页面。 
4.  选择\#no\_loose\_sentinel-enabled，将其状态修改为yes即可开启。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64891/154339706332844_zh-CN.png) 

    **说明：** 

    -   目前2.8版本实例暂不支持sentinel兼容模式。

    -   如果您的4.0版本实例不支持sentinel兼容模式，建议升级小版本。

    -   社区sentinel无需密码验证，一般支持sentinel的客户端没有auth过程。云Redis本身兼容sentinel模式，故需要密码验证，目前仅支持在VPC免密下客户端才能访问Redis。开启VPC免密方法见下图。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64891/154339706333162_zh-CN.png)


