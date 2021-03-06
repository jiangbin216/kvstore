# Redis-benchmark使用介绍 {#concept_zm4_dy5_ydb .concept}

Redis-benchmark是官方自带的Redis性能测试工具，可以有效的测试Redis服务的性能。

使用说明如下：

```
Usage: redis-benchmark [-h] [-p] [-c] [-n[-k]
 -h     Server hostname (default 127.0.0.1)
 -p     Server port (default 6379)
 -s     Server socket (overrides host and port)
 -c     Number of parallel connections (default 50)
 -n     Total number of requests (default 10000)
 -d      Data size of SET/GET value in bytes (default 2)
 -k      1=keep alive 0=reconnect (default 1)
 -r      Use random keys for SET/GET/INCR, random values for SADD
  Using this option the benchmark will get/set keys
  in the form mykey_rand:000000012456 instead of constant
  keys, the argument determines the max
  number of values for the random number. For instance
  if set to 10 only rand:000000000000 - rand:000000000009
  range will be allowed.
 -P       Pipelinerequests. Default 1 (no pipeline).
 -q       Quiet. Just show query/sec values
 —csv     Output in CSV format
 -l       Loop. Run the tests forever
 -t       Only run the comma-separated list of tests. The test
  names are the same as the ones produced as output.
 -I       Idle mode. Just open N idle connections and wait.
```

测试命令示例：

1.  ```
redis-benchmark -h 192.168.1.201 -p 6379 -c 100 -n 100000
```

    100个并发连接，100000个请求，检测host为localhost端口为6379的redis服务器性能。

2.  ```
redis-benchmark -h 192.168.1.201 -p 6379 -q -d 100
```

    测试存取大小为100字节的数据包的性能。

3.  ```
redis-benchmark -t set,lpush -n 100000 -q
```

    只测试某些操作的性能。

4.  ```
redis-benchmark -n 100000 -q script load "redis.call(‘set’,’foo’,’bar’)"
```

    只测试某些数值存取的性能。


实测报错如下：`writing to socket: connection timed out`。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13934/15474443964247_zh-CN.png)

输入`netstat -an`看下端口是不是有很多，重启Redis实例释放连接数，然后重新测试。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13934/15474443964248_zh-CN.png)

若需技术支持，请联系[售后技术支持](https://selfservice.console.aliyun.com/ticket/createIndex.htm)。

