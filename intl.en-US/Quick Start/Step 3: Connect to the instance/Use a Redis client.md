# Use a Redis client {#concept_dys_yvb_5db .concept}

You can connect to the ApsaraDB for Redis instance by using clients of several programming languages.

The database service of ApsaraDB for Redis is fully compatible with Redis database service. Therefore, you can connect to both database services in similar ways. All clients that are compatible with Redis protocols support connections to ApsaraDB for Redis. You can use any of these clients according to your application features.

**Note:** 

-   ApsaraDB for Redis only supports connections over an internal network of Alibaba Cloud. Therefore, you have to install a Redis client on an ECS instance in the same VPC as an ApsaraDB for Redis instance, and connect the ECS instance to the ApsaraDB for Redis instance to perform data operations.
-   If you enable password-free access for instances in the same VPC, you can connect to databases of the ApsaraDB for Redis instance with on password.
-   Before you connect to the ApsaraDB for Redis instance by using a client, you must add the private IP address of the ECS instance to [a whitelist group of the ApsaraDB for Redis instance](../../../../reseller.en-US/User Guide/Manage instances/Set IP whitelists.md#).

For more information about Redis clients, visit [http://redis.io/clients](http://redis.io/clients).

-   [Jedis client](#section_bqv_lkc_5db)
-   [phpredis client](#section_fsv_lkc_5db)
-   [redis-py client](#section_rsv_lkc_5db)
-   [C or C++ client](#section_zsv_lkc_5db)
-   [.NET client](#section_cvv_lkc_5db)
-   [node-redis client](#section_lwv_lkc_5db)
-   [C\# client StackExchange.Redis](#section_uwv_lkc_5db)

## Jedis client {#section_bqv_lkc_5db .section}

You can use a Jedis client to connect to ApsaraDB for Redis in any of the following ways:

-   Single Jedis connection
-   JedisPool-based connection

To use a Jedis client to connect to an ApsaraDB for Redis instance, follow these steps:

1.  Download and install the Jedis client. For more information, see [Jedis](https://github.com/xetorthio/jedis/wiki/Getting-started).

2.  Example of single Jedis connection

    1.  Open the Eclipse client, create a project, and then enter the following code:

        ``` {#codeblock_ax0_rcj_l1h}
        import redis.clients.jedis.Jedis;
        public class jedistest {
        public static void main(String[] args) {
        try {
             String host = "xx.kvstore.aliyuncs.com";//You can view the endpoint in the console.
             int port = 6379;
             Jedis jedis = new Jedis(host, port);
             //Authentication information
             jedis.auth("password");//password
             String key = "redis";
             String value = "aliyun-redis";
             //Select a database. Default value: 0.
             jedis.select(1);
             //Set a key
             jedis.set(key, value);
             System.out.println("Set Key " + key + " Value: " + value);
             //Obtain the configured key value.
             String getvalue = jedis.get(key);
             System.out.println("Get Key " + key + " ReturnValue: " + getvalue);
             jedis.quit();
             jedis.close();
        } 
        catch (Exception e) {
         e.printStackTrace();
         }
        }
        }
        ```

    2.  Run the project. You have connected to ApsaraDB for Redis if you view the following result in the Eclipse console.

        ``` {#codeblock_la3_1y5_l1p}
        Set Key redis Value aliyun-redis
        Get Key redis ReturnValue aliyun-redis
        ```

        Afterward, you can use your local Jedis client to manage your ApsaraDB for Redis instance. You can also connect to your ApsaraDB for Redis instance by using JedisPool.

3.  **Example of JedisPool-based connection**

    1.  Open the Eclipse client, create a project, and then configure the pom file as follows:

        ``` {#codeblock_lv3_j1h_4y3}
        <dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>2.7.2</version>
        <type>jar</type>
        <scope>compile</scope>
        </dependency>
        ```

    2.  Add the following application to the project:

        ``` {#codeblock_ot0_dz7_5ox}
        import org.apache.commons.pool2.PooledObject;
        import org.apache.commons.pool2.PooledObjectFactory;
        import org.apache.commons.pool2.impl.DefaultPooledObject;
        import org.apache.commons.pool2.impl.GenericObjectPoolConfig;
        import redis.clients.jedis.HostAndPort;
        import redis.clients.jedis.Jedis;
        import redis.clients.jedis.JedisPool;
        import redis.clients.jedis.JedisPoolConfig;
        ```

    3.  If your Jedis client version is Jedis-2.7.2, enter the following code in the project:

        ``` {#codeblock_lfx_pzb_ulf}
        JedisPoolConfig config = new JedisPoolConfig();
        //Maximum number of idle connections. You can customize this parameter. Make sure that the specified maximum number of idle connections does not exceed the maximum number of connections that the ApsaraDB for Redis instance supports.
        config.setMaxIdle(200);
        //Maximum number of connections. You can customize this parameter. Make sure that the specified maximum number of connections does not exceed the maximum number of connections that the ApsaraDB for Redis instance supports.
        config.setMaxTotal(300);
        config.setTestOnBorrow(false);
        config.setTestOnReturn(false);
        String host = "*.aliyuncs.com";
        String password = "Password";
        JedisPool pool = new JedisPool(config, host, 6379, 3000, password);
        Jedis jedis = null;
        try {
        jedis = pool.getResource();
        /// ... do stuff here ... for example
        jedis.set("foo", "bar");
        String foobar = jedis.get("foo");
        jedis.zadd("sose", 0, "car");
        jedis.zadd("sose", 0, "bike");
        Set<String> sose = jedis.zrange("sose", 0, -1);
        } finally {
        if (jedis ! = null) {
        jedis.close();
        }
        }
        /// ... when closing your application:
        pool.destroy();
        ```

    4.  If your Jedis client version is Jedis-2.6 or Jedis-2.5, enter the following code in the project:

        ``` {#codeblock_a0o_vfh_aa1}
        JedisPoolConfig config = new JedisPoolConfig();
        //Maximum number of idle connections. You can customize this parameter. Make sure that the specified maximum number of idle connections does not exceed the maximum number of connections that the ApsaraDB for Redis instance supports.
        config.setMaxIdle(200);
        //Maximum number of connections. You can customize this parameter. Make sure that the specified maximum number of connections does not exceed the maximum number of connections that the ApsaraDB for Redis instance supports.
        config.setMaxTotal(300);
        config.setTestOnBorrow(false);
        config.setTestOnReturn(false);
        String host = "*.aliyuncs.com";
        String password = "Password";
        JedisPool pool = new JedisPool(config, host, 6379, 3000, password);
        Jedis jedis = null;
        boolean broken = false;
        try {
             jedis = pool.getResource();
             /// ... do stuff here ... for example
             jedis.set("foo", "bar");
             String foobar = jedis.get("foo");
             jedis.zadd("sose", 0, "car");
             jedis.zadd("sose", 0, "bike");
             Set<String> sose = jedis.zrange("sose", 0, -1);
        } 
        catch (Exception e)
        {
             broken = true;
        } finally {
        if (broken) {
             pool.returnBrokenResource(jedis);
        } else if (jedis ! = null) {
             pool.returnResource(jedis);
         }
        }
        ```

    5.  Run the project. You have connected to ApsaraDB for Redis if you view the following result in the Eclipse console.

        ``` {#codeblock_0jl_v0w_b3t}
        Set Key redis Value aliyun-redis
        Get Key redis ReturnValue aliyun-redis
        ```

        Afterward, you can use your local Jedis client to manage your ApsaraDB for Redis instance.


## phpredis client {#section_fsv_lkc_5db .section}

To use a phpredis client to connect to an ApsaraDB for Redis instance, follow these steps:

1.  Download and install the phpredis client. For more information, see [phpredis](https://github.com/phpredis/phpredis).

2.  In any editor that supports PHP editing, enter the following code:

    ``` {#codeblock_f3l_rx6_ox3}
    <? php
     /* Replace the following parameter values with the host name and port number of the target instance. */
     $host = "localhost";
     $port = 6379;
     /* Replace the following parameter values with the ID and password of the target instance. */
     $user = "test_username";
     $pwd = "test_password";
     $redis = new Redis();
     if ($redis->connect($host, $port) == false) {
             die($redis->getLastError());
       }
     if ($redis->auth($pwd) == false) {
             die($redis->getLastError());
      }
      /* You can perform database operations after authentication. For more information, visit https://github.com/phpredis/phpredis. */
     if ($redis->set("foo", "bar") == false) {
             die($redis->getLastError());
     }
     $value = $redis->get("foo");
     echo $value;
     ? >
    ```

3.  Run the code. Afterward, you can use your local phpredis client to connect to your ApsaraDB for Redis instance. For more information, visit [https://github.com/phpredis/phpredis](https://github.com/phpredis/phpredis).

## redis-py client {#section_rsv_lkc_5db .section}

To use a redis-py client to connect to an ApsaraDB for Redis instance, follow these steps:

1.  Download and install the redis-py client. For more information, see [redis-py](https://github.com/andymccurdy/redis-py).

2.  In any editor that supports Python editing, enter the following code. Afterward, you can use the local redis-py client to connect to the ApsaraDB for Redis instance and perform database operations.


``` {#codeblock_dpp_xwn_egl}
#! /usr/bin/env python
#-*- coding: utf-8 -*-
import redis
#Replace the following parameter values with the host name and port number of the target instance.
host = 'localhost'
port = 6379
#Replace the following parameter value with the password of the target instance.
pwd = 'test_password'
r = redis.StrictRedis(host=host, port=port, password=pwd)
#You can perform database operations after you establish a connection. For more information, visit https://github.com/andymccurdy/redis-py.
r.set('foo', 'bar');
print r.get('foo')
```

## C or C++ client {#section_zsv_lkc_5db .section}

To use a C or C++ client to connect to an ApsaraDB for Redis instance, follow these steps:

1.  Download, compile, and install the C client by using the following code:

    ``` {#codeblock_5s5_ovk_r4c}
         git clone https://github.com/redis/hiredis.git
         cd hiredis
         make 
         sudo make install
    ```

2.  Enter the following code in the C or C++ editor:

    ``` {#codeblock_ht0_9kh_4zj}
         #include <stdio.h>
         #include <stdlib.h>
         #include <string.h>
         #include <hiredis.h>
         int main(int argc, char **argv) {
         unsigned int j;
         redisContext *c;
         redisReply *reply;
         if (argc < 4) {
                 printf("Usage: example xxx.kvstore.aliyuncs.com 6379 instance_id password\n");
                 exit(0);
         }
         const char *hostname = argv[1];
         const int port = atoi(argv[2]);
         const char *instance_id = argv[3];
         const char *password = argv[4];
         struct timeval timeout = { 1, 500000 }; // 1.5 seconds
         c = redisConnectWithTimeout(hostname, port, timeout);
         if (c == NULL || c->err) {
         if (c) {
                 printf("Connection error: %s\n", c->errstr);
                 redisFree(c);
         } else {
                 printf("Connection error: can't allocate redis context\n");
         }
         exit(1);
         }
         /* AUTH */
         reply = redisCommand(c, "AUTH %s", password);
         printf("AUTH: %s\n", reply->str);
         freeReplyObject(reply);
         /* PING server */
         reply = redisCommand(c,"PING");
         printf("PING: %s\n", reply->str);
         freeReplyObject(reply);
         /* Set a key */
         reply = redisCommand(c,"SET %s %s", "foo", "hello world");
         printf("SET: %s\n", reply->str);
         freeReplyObject(reply);
         /* Set a key using binary safe API */
         reply = redisCommand(c,"SET %b %b", "bar", (size_t) 3, "hello", (size_t) 5);
         printf("SET (binary API): %s\n", reply->str);
         freeReplyObject(reply);
         /* Try a GET and two INCR */
         reply = redisCommand(c,"GET foo");
         printf("GET foo: %s\n", reply->str);
         freeReplyObject(reply);
         reply = redisCommand(c,"INCR counter");
         printf("INCR counter: %lld\n", reply->integer);
         freeReplyObject(reply);
         /* again ... */
         reply = redisCommand(c,"INCR counter");
         printf("INCR counter: %lld\n", reply->integer);
         freeReplyObject(reply);
         /* Create a list of numbers, from 0 to 9 */
         reply = redisCommand(c,"DEL mylist");
         freeReplyObject(reply);
         for (j = 0; j < 10; j++) {
                 char buf[64];
                 snprintf(buf,64,"%d",j);
                 reply = redisCommand(c,"LPUSH mylist element-%s", buf);
                 freeReplyObject(reply);
             }
         /* Let's check what we have inside the list */
         reply = redisCommand(c,"LRANGE mylist 0 -1");
         if (reply->type == REDIS_REPLY_ARRAY) {
                 for (j = 0; j < reply->elements; j++) {
                 printf("%u) %s\n", j, reply->element[j]->str);
         }
         }
         freeReplyObject(reply);
         /* Disconnects and frees the context */
         redisFree(c);
         return 0;
         }
    ```

3.  Compile the code.

    ``` {#codeblock_w48_del_wbi}
    gcc -o example -g example.c -I /usr/local/include/hiredis -lhiredis
    ```

4.  Test the code.

    ``` {#codeblock_5mi_phk_dej}
     example xxx.kvstore.aliyuncs.com 6379 instance_id password
    ```


Now, the C or C++ client is connected to the ApsaraDB for Redis instance.

## .NET client {#section_cvv_lkc_5db .section}

To use a .NET client to connect to an ApsaraDB for Redis instance, follow these steps:

1.  Download and use the .NET client.

    ``` {#codeblock_ogo_sl6_2k6}
     git clone https://github.com/ServiceStack/ServiceStack.Redis
    ```

2.  Create a .NET project on the .NET client.

3.  Add the reference file stored in the library file directory ServiceStack.Redis/lib/tests to the client.

4.  Enter the following code in the .NET project to connect to the ApsaraDB for Redis instance. For more information about API operations, visit [https://github.com/ServiceStack/ServiceStack.Redis](https://github.com/ServiceStack/ServiceStack.Redis).

    ``` {#codeblock_1id_yd7_34e}
    using System;
     using System.Collections.Generic;
     using System.Linq;
     using System.Text;
     using System.Threading.Tasks;
     using ServiceStack.Redis;
     namespace ServiceStack.Redis.Tests
     {
             class Program
     {
     public static void RedisClientTest()
     {
             string host = "127.0.0.1";/*IP address of the host that you want to connect to*/
             string password = "password";/*Password*/
             RedisClient redisClient = new RedisClient(host, 6379, password);
             string key = "test-aliyun";
             string value = "test-aliyun-value";
             redisClient.Set(key, value);
             string listKey = "test-aliyun-list";
             System.Console.WriteLine("set key " + key + " value " + value);
             string getValue = System.Text.Encoding.Default.GetString(redisClient.Get(key));
             System.Console.WriteLine("get key " + getValue);
             System.Console.Read();
     }
     public static void RedisPoolClientTest()
     {
             string[] testReadWriteHosts = new[] {
             "redis://password@127.0.0.1:6379"/*redis://Password@IP address that you want to connect to:Port*/
     };
     RedisConfig.VerifyMasterConnections = false;//You must set the parameter.
     PooledRedisClientManager redisPoolManager = new PooledRedisClientManager(10/*Number of connections in the pool*/, 10/*Connection pool timeout value*/, testReadWriteHosts);
     for (int i = 0; i < 100; i++){
             IRedisClient redisClient = redisPoolManager.GetClient();//Obtain the connection.
             RedisNativeClient redisNativeClient = (RedisNativeClient)redisClient;
             redisNativeClient.Client = null;  //ApsaraDB for Redis does not support the CLIENT SETNAME command. Set Client to null.
     try
     {
             string key = "test-aliyun1111";
             string value = "test-aliyun-value1111";
             redisClient.Set(key, value);
             string listKey = "test-aliyun-list";
             redisClient.AddItemToList(listKey, value);
             System.Console.WriteLine("set key " + key + " value " + value);
             string getValue = redisClient.GetValue(key);
             System.Console.WriteLine("get key " + getValue);
             redisClient.Dispose();//
     }catch (Exception e)
     {
             System.Console.WriteLine(e.Message);
     }
     }
             System.Console.Read();
     }
     static void Main(string[] args)
     {
             //Single-connection mode
             RedisClientTest();
             //Connection-pool mode
             RedisPoolClientTest();
     }
     }
     }
    ```


## node-redis client {#section_lwv_lkc_5db .section}

To use a node-redis client to connect to an ApsaraDB for Redis instance, follow these steps:

1.  Download and install a node-redis client.

    ``` {#codeblock_3yl_ovg_ito}
    npm install hiredis redis
    ```

2.  Enter and run the following code on the node-redis client to connect to the ApsaraDB for Redis instance.

    ``` {#codeblock_nvk_w42_id5}
     var redis = require("redis"),
     client = redis.createClient(<port>, <"host">, {detect_buffers: true});
     client.auth("password", redis.print)
    ```

    **Note:** In the code, the port field specifies the port of the ApsaraDB for Redis instance. Default value: 6379. The host field specifies the endpoint of the ApsaraDB for Redis instance. The following example shows the settings of the port and host fields:

    ``` {#codeblock_9lu_r1r_578}
    client = redis.createClient(6379, "r-abcdefg.redis.rds.aliyuncs.com", {detect_buffers: true});
    ```

3.  Use the ApsaraDB for Redis instance.

    ``` {#codeblock_cxb_ijs_7ar}
       // Write data to the instance.
     client.set("key", "OK");
     // Query data on the instance. The instance returns data of String type.
     client.get("key", function (err, reply) {
     console.log(reply.toString()); // print `OK`
     });
     // If you specify a buffer, the instance returns a buffer.
     client.get(new Buffer("key"), function (err, reply) {
     console.log(reply.toString()); // print `<Buffer 4f 4b>`
     });
     client.quit();
    ```


## C\# client StackExchange.Redis {#section_uwv_lkc_5db .section}

To use the C\# client StackExchange.Redis to connect to an ApsaraDB for Redis instance, follow these steps:

1.  Download and install [StackExchange. Redis](https://github.com/StackExchange/StackExchange.Redis?spm=5176.100239.blogcont272212.10.IsQwET&file=StackExchange.Redis).

2.  Add a reference.

``` {#codeblock_vz3_k55_xwc}
using StackExchange.Redis;
```

3.  Initialize ConnectionMultiplexer.

    ConnectionMultiplexer is the core of StackExchange.Redis, and shared in the entire application. You must use ConnectionMultiplexer as a singleton. ConnectionMultiplexer is initialized in the following way:

    ``` {#codeblock_qkn_lel_7n6}
     // redis config
     private static ConfigurationOptions configurationOptions = ConfigurationOptions.Parse("127.0.0.1:6379,password=xxx,connectTimeout=2000");
      //the lock for singleton
     private static readonly object Locker = new object();
      //singleton
     private static ConnectionMultiplexer redisConn;
     //singleton
     public static ConnectionMultiplexer getRedisConn()
     {
         if (redisConn == null)
         {
             lock (Locker)
             {
                 if (redisConn == null || ! redisConn.IsConnected)
                 {
                     redisConn = ConnectionMultiplexer.Connect(configurationOptions);
                 }
             }
         }
         return redisConn;
     }
    ```

    **Note:** ConfigurationOptions contains multiple options, such as keepAlive, connectRetry, and name. For more information, see StackExchange.Redis.ConfigurationOptions.

4.  GetDatabase\(\) returns a lightweight object. You can obtain this object from the object of ConnectionMultiplexer.

    ``` {#codeblock_d9y_m14_cgd}
     redisConn = getRedisConn();
     var db = redisConn.GetDatabase();
    ```

5.  The following examples show five types of data structures. The API operations used in these examples are different from their usage in the native Redis service. These data structures include: string, hash, list, set, and sortedset.

    -   string

        ``` {#codeblock_p2g_zvf_whn}
        //set get
        string strKey = "hello";
        string strValue = "world";
        bool setResult = db.StringSet(strKey, strValue);
        Console.WriteLine("set " + strKey + " " + strValue + ", result is " + setResult);
        //incr
        string counterKey = "counter";
        long counterValue = db.StringIncrement(counterKey);
        Console.WriteLine("incr " + counterKey + ", result is " + counterValue);
        //expire
        db.KeyExpire(strKey, new TimeSpan(0, 0, 5));
        Thread.Sleep(5 * 1000);
        Console.WriteLine("expire " + strKey + ", after 5 seconds, value is " + db.StringGet(strKey));
        //mset mget
        KeyValuePair<RedisKey, RedisValue> kv1 = new KeyValuePair<RedisKey, RedisValue>("key1", "value1");
        KeyValuePair<RedisKey, RedisValue> kv2 = new KeyValuePair<RedisKey, RedisValue>("key2", "value2");
        db.StringSet(new KeyValuePair<RedisKey, RedisValue>[] {kv1,kv2});            
        RedisValue[] values = db.StringGet(new RedisKey[] {kv1.Key, kv2.Key});
        Console.WriteLine("mget " + kv1.Key.ToString() + " " + kv2.Key.ToString() + ", result is " + values[0] + "&&" + values[1]);
        ```

    -   hash

        ``` {#codeblock_zd5_gid_tmk}
        string hashKey = "myhash";
        //hset
        db.HashSet(hashKey,"f1","v1");
        db.HashSet(hashKey,"f2", "v2");
        HashEntry[] values = db.HashGetAll(hashKey);
        //hgetall
        Console.Write("hgetall " + hashKey + ", result is");
        for (int i = 0; i < values.Length;i++) 
        {
          HashEntry hashEntry = values[i];
          Console.Write(" " + hashEntry.Name.ToString() + " " + hashEntry.Value.ToString());
        }
        Console.WriteLine();
        ```

    -   list

        ``` {#codeblock_6tn_ogy_2p7}
        //list key
        string listKey = "myList";
        //rpush
        db.ListRightPush(listKey, "a");
        db.ListRightPush(listKey, "b");
        db.ListRightPush(listKey, "c");
        //lrange
        RedisValue[] values = db.ListRange(listKey, 0, -1);
        Console.Write("lrange " + listKey + " 0 -1, result is ");
        for (int i = 0; i < values.Length; i++)
        {
         Console.Write(values[i] + " ");
        }
        Console.WriteLine();
        ```

    -   set

        ``` {#codeblock_c65_kwu_lvx}
        //set key
        string setKey = "mySet";
        //sadd
        db.SetAdd(setKey, "a");
        db.SetAdd(setKey, "b");
        db.SetAdd(setKey, "c");
        //sismember
        bool isContains = db.SetContains(setKey, "a");
        Console.WriteLine("set " + setKey + " contains a is " + isContains );
        ```

    -   sortedset

        ``` {#codeblock_hrx_dml_ff5}
        string sortedSetKey = "myZset";
        //sadd
        db.SortedSetAdd(sortedSetKey, "xiaoming", 85);
        db.SortedSetAdd(sortedSetKey, "xiaohong", 100);
        db.SortedSetAdd(sortedSetKey, "xiaofei", 62);
        db.SortedSetAdd(sortedSetKey, "xiaotang", 73);
        //zrevrangebyscore
        RedisValue[] names = db.SortedSetRangeByRank(sortedSetKey, 0, 2, Order.Ascending);
        Console.Write("zrevrangebyscore " + sortedSetKey + " 0 2, result is ");
        for (int i = 0; i < names.Length; i++)
        {
          Console.Write(names[i] + " ");
        }
        Console.WriteLine();
        ```


