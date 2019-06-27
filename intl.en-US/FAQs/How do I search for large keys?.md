# How do I search for large keys? {#concept_frf_r2z_xdb .concept}

## Background {#section_t02_oal_qk1 .section}

ApsaraDB for Redis provides complex data structure types such as lists, hash tables, and sorted sets. When you use the service, improper key design may result in large keys. Due to Redis single-thread model, the operation to obtain or delete large keys may affect the service. In a cluster, large keys are prone to run out of memory of a certain node. Therefore, you can use a search tool to find large keys.

To scan for large keys of ApsaraDB for Redis, run the `SCAN` command for the master-replica edition or `ISCAN` command for the cluster edition. To obtain the number of nodes, run the `INFO` command. The command rules are as follows:

``` {#codeblock_zlm_krq_xuk}
ISCAN idx cursor [MATCH pattern] [COUNT count]
```

In this command, idx specifies the node ID that starts from 0. For an eight-node cluster instance of 16 GB to 64 GB, idx ranges from 0 to 7. A 128 GB or 256 GB cluster instance contains 16 nodes.

## Procedure {#section_shh_ikw_ey0 .section}

1.  Run the following command to download the Python client package:

    ``` {#codeblock_qcr_t1v_p5o}
    wget "https://pypi.python.org/packages/68/44/5efe9e98ad83ef5b742ce62a15bea609ed5a0d1caf35b79257ddb324031a/redis-2.10.5.tar.gz#md5=3b26c2b9703b4b56b30a1ad508e31083"
    ```

2.  Decompress the package and install the Python client.

    ``` {#codeblock_sgh_j92_otf}
     tar -xvf redis-2.10.5.tar.gz
     cd redis-2.10.5
     sudo python setup.py install
    ```

3.  Create the following scanning script:

    ``` {#codeblock_58u_pig_r7v}
     import sys
     import redis
     def check_big_key(r, k):
       bigKey = False
       length = 0 
       try:
         type = r.type(k)
         if type == "string":
           length = r.strlen(k)
         elif type == "hash":
           length = r.hlen(k)
         elif type == "list":
           length = r.llen(k)
         elif type == "set":
           length = r.scard(k)
         elif type == "zset":
           length = r.zcard(k)
       except:
         return
       if length > 10240:
         bigKey = True
       if bigKey :
         print db,k,type,length
     def find_big_key_normal(db_host, db_port, db_password, db_num):
       r = redis.StrictRedis(host=db_host, port=db_port, password=db_password, db=db_num)
       for k in r.scan_iter(count=1000):
         check_big_key(r, k)
     def find_big_key_sharding(db_host, db_port, db_password, db_num, nodecount):
       r = redis.StrictRedis(host=db_host, port=db_port, password=db_password, db=db_num)
       cursor = 0
       for node in range(0, nodecount) :
         while True:
           iscan = r.execute_command("iscan",str(node), str(cursor), "count", "1000")
           for k in iscan[1]:
             check_big_key(r, k)
           cursor = iscan[0]
           print cursor, db, node, len(iscan[1])
           if cursor == "0":
             break;
     if __name__ == '__main__':
       if len(sys.argv) ! = 4:
          print 'Usage: python ', sys.argv[0], ' host port password '
          exit(1)
       db_host = sys.argv[1]
       db_port = sys.argv[2]
       db_password = sys.argv[3]
       r = redis.StrictRedis(host=db_host, port=int(db_port), password=db_password)
       nodecount = r.info()['nodecount']
       keyspace_info = r.info("keyspace")
       for db in keyspace_info:
         print 'check ', db, ' ', keyspace_info[db]
         if nodecount > 1:
           find_big_key_sharding(db_host, db_port, db_password, db.replace("db",""), nodecount)
         else:
           find_big_key_normal(db_host, db_port, db_password, db.replace("db", ""))
    ```

4.  Run the `python find_bigkey <host> 6379 <password>` command to search for large keys.

    **Note:** 

    The command returns a list of large keys in the master-replica edition and cluster edition of ApsaraDB for Redis. The default threshold for large keys is 10,240. Large keys include string-type keys with a value greater than 10,240, list-type keys with a length greater than 10,240, or hash-type keys with more than 10,240 hash fields.

    By default, the script searches 1,000 keys to minimize the adverse impact on service performance. However, we recommend that you run the script during off-peak hours to prevent the adverse impact caused by running the SCAN command.


