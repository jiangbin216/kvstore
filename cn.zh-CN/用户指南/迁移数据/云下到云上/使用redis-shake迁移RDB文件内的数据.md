# 使用redis-shake迁移RDB文件内的数据 {#concept_188715 .concept}

使用redis-shake的restore模式，您可以将自建Redis的备份文件内的数据迁移到一个云数据库Redis版实例中，实现自建Redis上云。

## 前提条件 {#section_5yw_woo_qyl .section}

-   已创建作为迁移目的端的云数据库Redis版实例；
-   已创建用于运行redis-shake的ECS实例；
-   ECS实例可以访问目的Redis实例；
-   ECS实例的系统为Linux。
-   ECS中已经安装了git和golang。

## 背景信息 {#section_o6o_bml_4mz .section}

redis-shake是阿里云自研的开源工具，支持对Redis数据进行解析（decode）、恢复（restore）、备份（dump）、同步（sync/rump）。在restore模式下，redis-shake可以将RDB文件中保存的数据恢复到Redis实例中，实现数据恢复或者迁移，本文以将RDB文件中的数据恢复到云数据库Redis版实例中从而实现Redis上云迁移为例。

**说明：** 如需了解更多redis-shake相关信息，请参见[redis-shake Github主页](https://github.com/alibaba/RedisShake)。

## 操作步骤 {#section_qua_zm1_mx2 .section}

1.  登录可以连接云数据库Redis版实例（目的端Redis）的ECS。
2.  将redis-shake资源克隆到ECS。

    ``` {#codeblock_wca_cgc_wnx}
    # git clone https://github.com/alibaba/RedisShake.git
    ```

    ![](images/45575_zh-CN.png "将redis-shake资源git clone到ECS")

3.  切换到RedisShake目录并设置环境变量。

    ``` {#codeblock_twd_9j8_e1h}
    # cd RedisShake
    # export GOPATH=`pwd`
    ```

4.  切换到vendor目录，下载govendor并将其设置为可执行文件。

    ``` {#codeblock_ywx_asc_6io}
    # cd src/vendor
    # wget http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/94155/cn_zh/1556268861235/govendor
    # chmod u+x govendor
    ```

    **说明：** 如您已经安装了govendor请略过此步骤。

5.  执行`./govendor sync`并等待同步完成。
6.  切换到RedisShake目录编译文件。

    ``` {#codeblock_ote_lv8_42b}
    # cd ../../
    # ./build.sh
    ```

7.  修改配置文件conf/redis-shake.conf，涉及的参数及其说明如下。

    |参数|说明|
    |--|--|
    |input\_rdb|RDB文件的路径，可使用相对路径或绝对路径，例如/root/tools/RedisShake/demo.rdb。|
    |target.address|目的Redis的连接地址与端口号，例如`r-bp1xxxxxxxxxxxxx.redis.rds.aliyuncs.com:6379`。|
    |source.password\_raw|目的Redis的连接密码。|
    |target.db|要将数据恢复到的db，默认为0。例如，要将所有数据恢复到目的Redis的db10，则需将此参数的值设置为10。当该值小于0时，数据将恢复至db0。|
    |rewrite|当目的Redis有与RDB文件中相同的key，是否覆盖，可选值：     -   true（覆盖）；
    -   false（不覆盖）。
 **说明：** 默认为true，建议对目的Redis中的有效数据进行完善的备份再执行恢复。如设置为false且存在数据冲突则会出现异常提示。

 |

    **说明：** 其它参数如无特殊情况保持默认即可。

8.  在RedisShake目录中使用如下命令进行迁移。

    ```
    # ./bin/redis-shake -type=restore -conf=conf/redis-shake.conf
    ```

    ![](images/45611_zh-CN.png "执行示例")

    **说明：** 日志中出现`restore: rdb done`表示数据恢复完成，此时按Ctrl+C退出执行即可。


