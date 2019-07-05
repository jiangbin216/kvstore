# How do I view the memory of child instances of an ApsaraDB for Redis cluster instance? {#concept_fhm_hfz_xdb .concept}

## Background {#section_jos_0w0_wxs .section}

An ApsaraDB for Redis cluster instance contains multiple nodes. You need to check the memory and the number of keys of each node. Alibaba Cloud provides the `iinfo` command for you to check performance of a specified node. In the future, you will be able to view the data of each node in the console.

``` {#codeblock_aq8_snd_n0i}
iinfo db_idx [section]
```

In the command, the value range of db\_idx is \[0, nodecount\). You can obtain the value of nodecount by running the INFO command. To set the section parameter, you can follow the way to set the section parameter for the INFO command of Redis.

## Procedure {#section_js7_8cr_ywb .section}

1.  Download the Python client package.

    ``` {#codeblock_hld_dgy_vgf}
    wget "https://pypi.python.org/packages/68/44/5efe9e98ad83ef5b742ce62a15bea609ed5a0d1caf35b79257ddb324031a/redis-2.10.5.tar.gz#md5=3b26c2b9703b4b56b30a1ad508e31083"
    ```

2.  Decompress the package and install the Python client.

    ``` {#codeblock_v3m_237_zqk}
    tar -xvf redis-2.10.5.tar.gz
     cd redis-2.10.5
     sudo python setup.py install
    ```

3.  Run the following scanning script:

    ``` {#codeblock_nwy_d3t_9vv}
     import sys
     import redis
     from redis._compat import nativestr
     def parse_info(response):
         "Parse the result of Redis's INFO command into a Python dict"
         info = {}
         response = nativestr(response)
         def get_value(value):
             if ',' not in value or '=' not in value:
                 try:
                     if '.' in value:
                         return float(value)
                     else:
                         return int(value)
                 except ValueError:
                     return value
             else:
                 sub_dict = {}
                 for item in value.split(','):
                     k, v = item.rsplit('=', 1)
                     sub_dict[k] = get_value(v)
                 return sub_dict
         for line in response.splitlines():
             if line and not line.startswith('#'):
                 if line.find(':') ! = -1:
                     key, value = line.split(':', 1)
                     info[key] = get_value(value)
                 else:
                     # if the line isn't splittable, append it to the "__raw__" key
                     info.setdefault('__raw__', []).append(line)
         return info
     if __name__ == '__main__':
       if len(sys.argv) ! = 4:
          print 'Usage: python ', sys.argv[0], ' host port password '
          exit(1)
       db_host = sys.argv[1]
       db_port = sys.argv[2]
       db_password = sys.argv[3]
       r = redis.StrictRedis(host=db_host, port=int(db_port), password=db_password)
       nodecount = r.info()['nodecount']
       for node in range(0, nodecount):
          info = r.execute_command("iinfo", str(node))
          info_res = parse_info(info)
          print "============ node ", str(node), " ================"
          print 'used_memory_human:', info_res['used_memory_human']
          print r.execute_command("iinfo", str(node), "keyspace")
       info_res = r.info()
       print "============ total  ================"
       print 'used_memory_human:', info_res['used_memory_human']
       print r.info('keyspace')
    ```

    Run the `python check_sharding_db host port password` command to output the following content:

    ``` {#codeblock_h76_o0c_hc9}
     ============ node  0  ================
     used_memory_human: 37.56M
     # Keyspace
     db0:keys=9887,expires=0,avg_ttl=0
     ============ node  1  ================
     used_memory_human: 37.58M
     # Keyspace
     db0:keys=9835,expires=0,avg_ttl=0
     Db1: Keys = 1, expires = 0, avg_ttl = 0
     ============ node  2  ================
     used_memory_human: 41.24M
     # Keyspace
     db0:keys=9956,expires=0,avg_ttl=0
     db1:keys=1,expires=0,avg_ttl=0
     ============ node  3  ================
     used_memory_human: 37.58M
     # Keyspace
     db0:keys=9863,expires=0,avg_ttl=0
     ============ node  4  ================ 
     used_memory_human: 37.61M
     # Keyspace
     db0:keys=10045,expires=0,avg_ttl=0
     ============ node  5  ================
     used_memory_human: 37.58M
     # Keyspace
     db0:keys=10038,expires=0,avg_ttl=0
     ============ node  6  ================
     used_memory_human: 37.58M
     # Keyspace
     db0:keys=10055,expires=0,avg_ttl=0
     ============ node  7  ================
     used_memory_human: 37.57M
     # Keyspace
     db0:keys=9969,expires=0,avg_ttl=0
     ============ total  ================
     used_memory_human: 304.31M
     {'db1': {'keys': 2, 'expires': 0, 'avg_ttl': 0}, 'db0': {'keys': 79648, 'expires': 0, 'avg_ttl': 0}}
    ```


