# ApsaraDB for Redis如何进行性能测试? {#concept_kml_c4v_ydb .concept}

您可以通过redis-benchmark命令来进行测试。

请您参考：

```
Usage: redis-benchmark [-h] [-p] [-c] [-n[-k]  
-h      Server hostname (default 127.0.0.1) 
-p      Server port (default 6379) 
-s       Server socket (overrides host and port) 
-c       Number of parallel connections (default 50) 
-n      Total number of requests (default 10000) 
-d      Data size of SET/GET value in bytes (default 2) 
-k      1=keep alive 0=reconnect (default 1) 
-r       Use random keys for SET/GET/INCR, random values for SADD 
  Using this option the benchmark will get/set keys 
  in the form mykey_rand:000000012456 instead of constant 
  keys, theargument determines the max 
  number of values for the random number. For instance 
  if set to 10 only rand:000000000000 - rand:000000000009 
  range will be allowed. 
-P   Pipelinerequests. Default 1 (no pipeline). 
-q   Quiet. Just show query/sec values 只显示每秒钟能处理多少请求数结果 
-csv   Output in CSV format 
-l    Loop. Run the tests forever 永久测试 
-t   Only run the comma separated list of tests. The test 
      names are the same as the ones produced as output. 
-I    Idle mode. Just open N idle connections and wait.
```

如果问题还存在，请联系[阿里云售后支持](https://selfservice.console.aliyun.com/ticket/createIndex.htm?spm=0.0.0.0.NRwAca)。

