# ModifyInstanceConfig {#reference_j1k_m22_xdb .reference}

调用该API可以修改实例的配置参数。

## 请求参数 {#section_fn4_gkw_wbb .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|<公共请求参数\>|-|是|参见[公共请求参数](intl.zh-CN/API 参考/公共参数.md#section_hph_dhp_wbb)。|
|Action|String|是|系统规定参数，取值：ModifyInstanceConfig。|
|InstanceId|String|是|实例 ID|
|Config|String|是|实例的配置参数（Json String）。参见 [实例配置参数表](intl.zh-CN/API 参考/附表/实例配置参数表.md#)。|

## 返回参数 {#section_e4w_jkw_wbb .section}

|名称|类型|描述|
|--|--|--|
|<公共返回参数\>|-|参见[公共返回参数](intl.zh-CN/API 参考/公共参数.md#section_rjr_zgp_wbb)。|

## 请求示例 {#section_d3l_4kw_wbb .section}

```
https://r-kvstore.aliyuncs.com
?<公共请求参数>
&Action= ModifyInstanceConfig
&InstanceId= de5d88e34d004211
&Config={"hash-max-ziplist-entries":"512"}
```

## 返回示例 {#section_hjp_tkw_wbb .section}

```
{
"RequestId":"59A58517-F8FF-44E5-B90F-F386DB3E4AB8"
}
```

