# Node连接Redis，用户认证提示错误“Ready check failed: NOAUTH Authentication required” {#concept_z44_vzv_ydb .concept}

Node客户端程序，在连接Redis的时候，提示错误信息“Error:Ready check failed: NOAUTH Authentication required”。例如下图：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13918/15475169414298_zh-CN.png)

从提示的错误信息，可以看出是认证失败了，auth这里填写的是Redis连接地址，正确的是写Redis实例ID。

一般认证失败需要从两方面进行检查。

1.  配置的密码是否正确。
2.  认证的用户密码，是Redis实例ID加密码的方式，检查格式是否正确。

    参考Redis控制台显示的连接密码。


如果问题还未能解决，请联系[售后技术支持](https://selfservice.console.aliyun.com/ticket/createIndex.htm?spm=0.0.0.0.IRs9JQ)。

