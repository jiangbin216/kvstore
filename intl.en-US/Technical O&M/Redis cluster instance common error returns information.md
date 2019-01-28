# Redis cluster instance common error returns information {#concept_qgh_l1w_ydb .concept}

The following is a list of some of the errors that are frequently encountered during the use of the Ali cloud redis cluster edition instance return information, helps users identify and troubleshoot similar problems encountered in actual operations.

-   DB is read-only and mainly occurs in the process of instance variation, iteration upgrade, and so on.

```
Now you can't write against a non-write redis
```

-   The instance is currently locked, typically due to user fees.

```
Disable you can't write or read against a disable instance
```

-   The value requested by redis cannot exceed 500 mb, and returns the following error message.

```
Redis fail or response big than 500 mb
```

-   The following error messages appear primarily in commands such as iinfo, riinfo, iscan, iMonitor, and so on, the index used to specify the node is not in the Legal range.

    ```
    Node idx is invalid
    Node num specified> = node count
    ```

-   In the redis cluster instance, commands such as transactions, scripts, and so on require that all keys be in the same slot, if you are not in the same slot, the following error message is returned.

    ```
    Command keys must in same slot
    ```

-   The eval and evalsha commands must have at least one key and the numkeys parameter is greater than 0.

```
For redis cluster, Eval/evalsha number of keys can't be negative or zero
```

-   Too many unprocessed requests have been stacked on the back end, and new requests have been rejected. The reason is that the client uses unreasonable pipeline.

    ```
    Request admitted, too many pending request
    ```


