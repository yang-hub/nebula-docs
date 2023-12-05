# SHOW QUERIES

The `show queries` statement lists all the running queries on your current GQL-server. It is beneficial for identifying any resource-intensive, prolonged queries that may be utilizing significant CPU resources.

## Syntax

```
SHOW QUERIES
```

or

```
CALL show_queries() RETURN *
```

## Parameters

- The `show_queries()` procedure returns a table with details about all queries currently running on the GQL-server. For more details, see [show_queries()](../../procedures/show-quereis.md).
- `*` specifies all queries currently running on the GQL-server.

## Query status

- `RUNNING`: The query is currently executing.
- `KILLING`: The query is being terminated.

## Examples

### Show all queries

Input:

```
SHOW QUERIES
```


Output:

```
+--------+------------------+-----------+---------------------+-----------------------------+---------------------------------------------------------------+----------------------------+--------------+-----------+
| User   | Host             | HomeGraph | SessionId           | QueryId                     | Query                                                         | StartTime                  | Duration(ms) | Status    |
+--------+------------------+-----------+---------------------+-----------------------------+---------------------------------------------------------------+----------------------------+--------------+-----------+
| "root" | "192.x.x.x:3713" | "empty"   | 4886098754931859754 | "20231128_06285900000z3tjb" | "use sf01 match (v:Person)-[:KNOWS]-{20}(b) limit 1 return v" | 2023-11-28T06:28:59.694000 | 10105        | "RUNNING" |
+--------+------------------+-----------+---------------------+-----------------------------+---------------------------------------------------------------+----------------------------+--------------+-----------+

```

### Show all queries using the `show_queries()` procedure

Input:

```
CALL show_queries() RETURN *
```

Output:

```
+--------+------------------+-----------+---------------------+-----------------------------+---------------------------------------------------------------+----------------------------+--------------+-----------+
| User   | Host             | HomeGraph | SessionId           | QueryId                     | Query                                                         | StartTime                  | Duration(ms) | Status    |
+--------+------------------+-----------+---------------------+-----------------------------+---------------------------------------------------------------+----------------------------+--------------+-----------+
| "root" | "192.x.x.x:3713" | "empty"   | 4886098754931859754 | "20231128_06303700005z3tjb" | "use sf01 match (v:Person)-[:KNOWS]-{20}(b) limit 1 return v" | 2023-11-28T06:30:37.519000 | 1739         | "RUNNING" |
+--------+------------------+-----------+---------------------+-----------------------------+---------------------------------------------------------------+----------------------------+--------------+-----------+
```
