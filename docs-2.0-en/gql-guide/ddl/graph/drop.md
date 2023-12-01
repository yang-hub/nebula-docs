# DROP GRAPH

`DROP GRAPH` is used to drop a graph.

## Synatx

### `<drop graph type statement>`

```
<drop graph statement> ::=
    DROP [ PROPERTY ] GRAPH [ IF EXISTS ] <catalog graph parent and name>
```

## Prerequisites

To drop a graph, you must have `CREATE` privilege in the used schema.

## Effects

`DROP GRAPH` will drop the given graph from the catalog. The graph data will be deleted asynchronously.

## Parameters

### `IF EXISTS`

When `IF EXISTS` not specified, an error will be returned if the given graph does not exists.

## Example

```
DROP GRAPH g1
```

Drop the graph `g1`.